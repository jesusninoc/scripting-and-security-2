# Ejecutar código JavaScript en Base64 utilizando Start-Process y Google Chrome en PowerShell
## JavaScript, PowerShell 
### URL: https://www.jesusninoc.com/2016/10/31/ejecutar-codigo-javascript-en-base64-utilizando-start-process-y-google-chrome-en-powershell/
```PowerShell
$contenido="data:text/html;base64,PHNjcmlwdD5hbGVydChEYXRlKCkpPC9zY3JpcHQ+"
Start-Process chrome $contenido

```
