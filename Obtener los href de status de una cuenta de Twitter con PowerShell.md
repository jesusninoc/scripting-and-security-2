# Obtener los href de status de una cuenta de Twitter con PowerShell
## PowerShell, Web, Web scraping 
### URL: https://www.jesusninoc.com/2017/08/09/obtener-los-href-de-status-de-una-cuenta-de-twitter-con-powershell/
```PowerShell
$web=Invoke-WebRequest "https://twitter.com/microsoft"
$web.Links | Where-Object {$_.href -match "status"} | Select-Object href | %{$_}

```
