# Obtener la posición GPS de una calle con PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2017/07/25/obtener-la-posicion-gps-de-una-calle-con-powershell/
```PowerShell
$calle='Avenida%20de%20Concha%20Espina%201'
$ciudad='Madrid'
$urlsi="https://maps.googleapis.com/maps/api/geocode/json?address=" + $calle + “+” + $ciudad 
$result=(Invoke-WebRequest -Uri $urlsi).Content | ConvertFrom-JSON
$result.results."geometry".location

```
