# Mostrar los precios de la sesión del IBEX 35 creando un servidor web al que se pueda acceder desde cualquier parte de la red privada con PowerShell
## Network, PowerShell, Servers, Web 
### URL: https://www.jesusninoc.com/2017/05/17/mostrar-los-precios-de-la-sesion-del-ibex-35-creando-un-servidor-web-al-que-se-pueda-acceder-desde-cualquier-parte-de-la-red-privada-con-powershell/
```PowerShell
#PowerShell
#Ejecutar PowerShell como administrador

$web=Invoke-WebRequest 'http://www.bolsamadrid.es/esp/aspx/Mercados/Precios.aspx?indice=ESI100000000'

$routes = @{
    "/" = { return '<html><body>'+($web.AllElements | Where Class -eq “TblPort” | %{$_.outerHTML})+'</body></html>' }
}

#Importante poner la IP de la red privada
$url = 'http://192.168.1.157:8080/'
$listener = New-Object System.Net.HttpListener
$listener.Prefixes.Add($url)
$listener.Start()

Write-Host "Funcionando $url..."

Start-Process chrome $url

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
