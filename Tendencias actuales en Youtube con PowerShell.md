# Tendencias actuales en Youtube con PowerShell
## PowerShell, Web, Web scraping 
### URL: https://www.jesusninoc.com/2016/11/29/tendencias-actuales-en-youtube-con-powershell/
```PowerShell
$url="https://www.google.es/trends/"
$result = Invoke-WebRequest $url
$result.AllElements | Where Class -eq “single-video-title hottrends-single-trend-title ellipsis-maker-inner” | %{$_.innerText}

```
