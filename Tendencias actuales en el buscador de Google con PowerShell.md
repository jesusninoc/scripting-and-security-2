# Tendencias actuales en el buscador de Google con PowerShell
## PowerShell, Web, Web scraping 
### URL: https://www.jesusninoc.com/2016/11/27/tendencias-actuales-en-el-buscador-de-google-con-powershell/
```PowerShell
$url="https://www.google.es/trends/"
$result = Invoke-WebRequest $url
$result.AllElements | Where Class -eq “hottrends-single-trend-title ellipsis-maker-inner” | %{$_.innerText}

```
