# Realizar una redirección con JavaScript utilizando Start-Process y Google Chrome
## JavaScript, PowerShell 
### URL: https://www.jesusninoc.com/2017/02/06/realizar-una-redireccion-con-javascript-utilizando-start-process-y-google-chrome-2/
```PowerShell
$contenido="data:text/html,<script>top.location.href='https://www.jesusninoc.com';</script>"
Start-Process chrome $contenido

```
# Realizar una redirección con JavaScript utilizando Start-Process y Google Chrome
## JavaScript, PowerShell 
### URL: https://www.jesusninoc.com/2016/11/02/realizar-una-redireccion-con-javascript-utilizando-start-process-y-google-chrome/
```PowerShell
$contenido="data:text/html,<script>top.location.href='https://www.jesusninoc.com';</script>"
Start-Process chrome $contenido

##############################
#Las comillas así no funcionan
##############################
$contenido='data:text/html,<script>top.location.href="https://www.jesusninoc.com";</script>'
Start-Process chrome $contenido

```
