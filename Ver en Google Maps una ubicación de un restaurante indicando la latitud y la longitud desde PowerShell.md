# Ver en Google Maps una ubicación de un restaurante indicando la latitud y la longitud desde PowerShell
## PowerShell, Web 
### URL: https://www.jesusninoc.com/2018/06/07/ver-en-google-maps-una-ubicacion-de-un-restaurante-indicando-la-latitud-y-la-longitud-desde-powershell/
```PowerShell
$calle='Zen Market'
$ciudad='Madrid'
$urlsi="https://maps.googleapis.com/maps/api/geocode/json?address=" + $calle + “+” + $ciudad 
$result=(Invoke-WebRequest -Uri $urlsi).Content | ConvertFrom-JSON
$posicion=$result.results."geometry".location
$metros="703m"
Start-Process chrome "https://www.google.es/maps/@$($posicion.lat),$($posicion.lng),$metros/data=!3m1!1e3"

```
