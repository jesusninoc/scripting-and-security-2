# Detectar la versión de WordPress leyendo desde un fichero cada dominio en PowerShell
## PowerShell, Security, Web, Web scraping 
### URL: https://www.jesusninoc.com/2017/03/24/detectar-la-version-de-wordpress-leyendo-desde-un-fichero-cada-dominio-en-powershell/
```PowerShell
gc .\webs.txt | %{
$web=Invoke-WebRequest $_
Write-Host $_,":", ($web.ParsedHtml.head.getElementsByTagName('meta') | ? name -EQ "generator").content
}

```
