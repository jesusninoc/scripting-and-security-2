# Realizar una redirección con JavaScript en Base64 utilizando Start-Process y Google Chrome
## JavaScript, PowerShell 
### URL: https://www.jesusninoc.com/2016/11/04/realizar-una-redireccion-con-javascript-en-base64-utilizando-start-process-y-google-chrome/
```PowerShell
################################
#El código de la redirección es:
#<script>top.location.href="https://www.jesusninoc.com";</script>
################################
$contenido="data:text/html;base64,PHNjcmlwdD50b3AubG9jYXRpb24uaHJlZj0iaHR0cDovL3d3dy5qZXN1c25pbm9jLmNvbSI7PC9zY3JpcHQ+"
Start-Process chrome $contenido

################################
#El código de la redirección es:
#<script>top.location.href='https://www.jesusninoc.com';</script>
################################
$contenido='data:text/html;base64,PHNjcmlwdD50b3AubG9jYXRpb24uaHJlZj0naHR0cDovL3d3dy5qZXN1c25pbm9jLmNvbSc7PC9zY3JpcHQ+'
Start-Process chrome $contenido

```
