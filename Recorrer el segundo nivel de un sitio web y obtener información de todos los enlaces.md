# Recorrer el segundo nivel de un sitio web y obtener información de todos los enlaces
## Automation, PowerShell, Web 
### URL: https://www.jesusninoc.com/2017/11/14/recorrer-el-segundo-nivel-de-un-sitio-web-y-obtener-informacion-de-todos-los-enlaces/
```PowerShell
$url="http://www.jesusninoc.com"
foreach($links in (Invoke-WebRequest $url).Links.href){foreach($links2 in (Invoke-WebRequest $links).Links.href){$links2,(Invoke-WebRequest $links2).RawContentLength,2}}

```
