# Cargar un iframe utilizando Start-Process y Google Chrome
## PowerShell 
### URL: https://www.jesusninoc.com/2017/02/08/cargar-un-iframe-utilizando-start-process-y-google-chrome/
```PowerShell
$contenido="data:text/html,<html><body><iframe%20frameborder='0'%20scrolling='no'%20src='https://www.jesusninoc.com'%20width='100%'%20height='800'></iframe></body></html>"
Start-Process chrome $contenido

```
