# Listas de búsquedas populares de 2015 en Google con PowerShell
## PowerShell, Web, Web scraping 
### URL: https://www.jesusninoc.com/2016/11/30/listas-de-busquedas-populares-de-2015-en-google-con-powershell/
```PowerShell
$url="https://www.google.es/trends/"
$result = Invoke-WebRequest $url
$result.AllElements | Where Class -eq “topcharts-smallchart-entity-title-in-list” | %{$_.innerText}

```
