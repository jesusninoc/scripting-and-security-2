# Mostrar la versión de WordPress con PowerShell
## PowerShell, Security, Web, Web scraping 
### URL: https://www.jesusninoc.com/2017/02/26/mostrar-la-version-de-wordpress-con-powershell/
```PowerShell
$web=Invoke-WebRequest 'https://www.jesusninoc.com'
($web.ParsedHtml.head.getElementsByTagName('meta') | ? name -EQ "generator").content

```
