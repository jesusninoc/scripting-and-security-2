# Mostrar los últimos tuits de una cuenta creando un servidor web al que se pueda acceder desde cualquier parte de la red privada con PowerShell
## Network, PowerShell, Servers, Web 
### URL: https://www.jesusninoc.com/2017/05/24/mostrar-los-ultimos-tuits-de-una-cuenta-creando-un-servidor-web-al-que-se-pueda-acceder-desde-cualquier-parte-de-la-red-privada-con-powershell/
```PowerShell
#PowerShell
#Ejecutar PowerShell como administrador

#JSON Twitter
$numero="490274947189993472"
while($numero)
{
$numero
$ur='https://twitter.com/i/profiles/show/Microsoft/timeline?include_available_features=1&include_entities=1&max_id='+$numero
$result=(Invoke-WebRequest -Uri $ur)
$conv=$result.Content
$convi = $conv | ConvertFrom-JSON
#Max id
$numero=$convi.max_id
#More items?
$convi.items_html
}

$routes = @{
    "/" = { return '<html><body>'+$convi.items_html+'</body></html>' }
}

#Importante poner la IP de la red privada
$url = 'http://192.168.1.157:8080/'
$listener = New-Object System.Net.HttpListener
$listener.Prefixes.Add($url)
$listener.Start()

Write-Host "Funcionando $url..."

Start-Process $url

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
