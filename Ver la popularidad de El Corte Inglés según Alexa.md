# Ver la popularidad de El Corte Inglés según Alexa
## PowerShell, Web, Web scraping 
### URL: https://www.jesusninoc.com/2017/04/05/ver-la-popularidad-de-el-corte-ingles-segun-alexa/
```PowerShell
((Invoke-WebRequest "https://www.alexa.com/siteinfo/corteingles.com").AllElements | Where class -eq “metrics-data align-vmiddle”)[0].innerText

```
