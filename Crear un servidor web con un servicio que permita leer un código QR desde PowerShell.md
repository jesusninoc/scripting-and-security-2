# Crear un servidor web con un servicio que permita leer un código QR desde PowerShell
## Network, PowerShell, Servers, Web 
### URL: https://www.jesusninoc.com/2018/06/05/crear-un-servidor-web-con-un-servicio-que-permita-leer-un-codigo-qr-desde-powershell/
```PowerShell
# Leer un código QR
# Las funciones JavaScript se han obtenido de webqr.com

# Descargar las funciones JavaScript al equipo
#Start-BitsTransfer "https://webqr.com/webqr.js"
#Start-BitsTransfer "https://webqr.com/llqrcode.js"

$routes = @{
    
    # Cargar las funciones JavaScript
    # Es necesario quitar el caracter // porque provoca un error al leer el fichero JS

    "/webqr.js" = { return (gc ./webqr.js) | % {if(!($_ -match "// " -or $_ -match "//document" )){$_}} }

    "/llqrcode.js" = { return (gc ./llqrcode.js) }

    # Cargar el código HTML

    "/" = { return '<html>
<head>
<title>QR Code scanner</title>

<style type="text/css">
body{
    width:100%;
    text-align:center;
}
#main{
    margin: 15px auto;
    background:white;
    overflow: auto;
	width: 100%;
}
#header{
    background:white;
    margin-bottom:15px;
}
#mainbody{
    background: white;
    width:100%;
	display:none;
}

#qr-canvas{
    display:none;
}

#mp1{
    text-align:center;
    font-size:35px;
}
#imghelp{
    position:relative;
    left:0px;
    top:-160px;
    z-index:100;
    font:18px arial,sans-serif;
    background:#f0f0f0;
	margin-left:35px;
	margin-right:35px;
	padding-top:10px;
	padding-bottom:10px;
	border-radius:20px;
}
.selector{
    margin:0;
    padding:0;
    cursor:pointer;
    margin-bottom:-5px;
}
#outdiv
{
    width:320px;
    height:240px;
	border: solid;
	border-width: 3px 3px 3px 3px;
}
#result{
    border: solid;
	border-width: 1px 1px 1px 1px;
	padding:20px;
	width:70%;
}

.tsel{
    padding:0;
}

</style>

<script type="text/javascript" src="llqrcode.js"></script>
<script type="text/javascript" src="webqr.js"></script>

</head>

<body>
<div id="main">
<div id="header">
<p id="mp1">QR Code scanner</p>
</div>
<div id="mainbody">
<table class="tsel" border="0" width="100%">
<tr>
<td valign="top" align="center" width="50%">
<table class="tsel" border="0">
<tr>
<td><div class="selector" onclick="setimg()" align="right"/>Scanner</td></tr>
<tr><td colspan="2" align="center">
<div id="outdiv">
</div></td></tr>
</table>
</td>
</tr>
<tr><td colspan="3" align="center">
<div id="result"></div>
</td></tr>
</table>
</div>
</div>
<canvas id="qr-canvas" width="800" height="600"></canvas>
<script type="text/javascript">load();</script>
</body>

</html>' }

}

$url = 'http://localhost:8080/'
$listener = New-Object System.Net.HttpListener
$listener.Prefixes.Add($url)
$listener.Start()

Write-Host "Funcionando $url..."

while ($listener.IsListening)
{
    $context = $listener.GetContext()
    $requestUrl = $context.Request.Url
    $con
    $response = $context.Response

    Write-Host ''
    Write-Host "Petición: $requestUrl"

    $localPath = $requestUrl.LocalPath
    $route = $routes.Get_Item($requestUrl.LocalPath)

    if ($route -eq $null)
    {
        $response.StatusCode = 404
    }
    else
    {
        $content = & $route
        $buffer = [System.Text.Encoding]::UTF8.GetBytes($content)
        $response.ContentLength64 = $buffer.Length
        $response.OutputStream.Write($buffer, 0, $buffer.Length)
    }
    
    $response.Close()

    $responseStatus = $response.StatusCode
    Write-Host "Respuesta: $responseStatus"
}

```
