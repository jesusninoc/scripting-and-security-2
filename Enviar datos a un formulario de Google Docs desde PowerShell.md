# Enviar datos a un formulario de Google Docs desde PowerShell
## Automation, PowerShell 
### URL: https://www.jesusninoc.com/2017/03/11/enviar-datos-a-un-formulario-de-google-docs-desde-powershell/
```PowerShell
$postParams = @{'entry.1681544078'='hola2'}
$web=Invoke-WebRequest -Uri 'https://docs.google.com/forms/d/e/1FAIpQLSdKkhEjsIRCAWGKCGKJN04OfYZGEI0PExx4KC44mZbwH6QJLw/formResponse' -Method Post -Body $postParams
$web.StatusCode

```
