# Ver la popularidad de LinkedIn según Alexa
## PowerShell, Web, Web scraping 
### URL: https://www.jesusninoc.com/2017/01/07/ver-la-popularidad-de-linkedin-segun-alexa/
```PowerShell
$url="https://www.alexa.com/siteinfo/linkedin.com"
$result = Invoke-WebRequest $url
($result.AllElements | Where class -eq “metrics-data align-vmiddle”)[0].innerText

```
