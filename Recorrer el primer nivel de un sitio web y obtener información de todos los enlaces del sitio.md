# Recorrer el primer nivel de un sitio web y obtener información de todos los enlaces del sitio
## Automation, PowerShell, Web 
### URL: https://www.jesusninoc.com/2017/12/03/recorrer-el-primer-nivel-de-un-sitio-web-y-obtener-informacion-de-todos-los-enlaces-del-sitio/
```PowerShell
$url="http://www.jesusninoc.com"
foreach($links in (Invoke-WebRequest $url).Links.href){($links,(Invoke-WebRequest $links).RawContentLength,1)}

```
