# Obtener con PowerShell los enlaces a los scripts en JavaScript (extensión .js) que tiene una web
## PowerShell, Web, Web scraping 
### URL: https://www.jesusninoc.com/2018/06/14/obtener-con-powershell-los-enlaces-a-los-scripts-en-javascript-extension-js-que-tiene-una-web/
```PowerShell
$web = Invoke-WebRequest "http://demo.owasp-juice.shop/#/search"

# Opción 1
$web.Scripts.src

# Opción 2
$web.Content -split "`n" | %{
    $_ | Select-String '\.js"'
}

```
