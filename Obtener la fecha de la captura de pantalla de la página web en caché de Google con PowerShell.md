# Obtener la fecha de la captura de pantalla de la página web en caché de Google con PowerShell
## PowerShell, Web 
### URL: https://www.jesusninoc.com/2017/02/19/obtener-la-fecha-de-la-captura-de-pantalla-de-la-pagina-web-en-cache-de-google-con-powershell/
```PowerShell
$url="https://webcache.googleusercontent.com/search?q=cache:www.jesusninoc.com/"
$result = Invoke-WebRequest $url
$result.AllElements | Where id -eq “google-cache-hdr” | %{$_.innerText}

```
