# Convertir un texto en código HTML
## PowerShell, Web 
### URL: https://www.jesusninoc.com/2017/05/22/convertir-un-texto-en-codigo-html/
```PowerShell
Add-Type -AssemblyName System.Web
[System.Web.HttpUtility]::HtmlEncode('Informationen über die Grafikkarte')
[System.Web.HttpUtility]::HtmlEncode('Información sobre la tarjeta gráfica')

```
