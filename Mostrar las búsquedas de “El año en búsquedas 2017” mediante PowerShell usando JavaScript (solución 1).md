# Mostrar las búsquedas de “El año en búsquedas 2017” mediante PowerShell usando JavaScript (solución 1)
## JavaScript, PowerShell 
### URL: https://www.jesusninoc.com/2018/01/03/mostrar-las-busquedas-de-el-ano-en-busquedas-2017-mediante-powershell-usando-javascript/
```PowerShell
$ie = New-Object -com "InternetExplorer.Application"
$ie.Navigate("About:blank")
$ie.visible = $true

$web=([System.Net.WebRequest]::Create("https://google.com/trends/embed/yis/2017/GLOBAL/3bc22de5-427e-4737-8e27-f96ee7d75edf?forceMobileMode=false&isPreviewMode=true&hl=es")).GetResponse().GetResponseStream()
$contenidoweb=New-Object System.IO.StreamReader $web
$htmlnew=$contenidoweb.ReadToEnd()+'<script>var Items = embedWidgetGlobals.data.listItems; alert(Items)</script>'

$ie.Document.write($htmlnew)

```
