# Convertir un array a CSV con PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2018/04/10/convertir-un-array-a-csv-con-powershell/
```PowerShell
$csv = @'  
fecha,nombre,correo
09/04/2018,Juan,juan@example.com,
14/04/2018,Marta,marta@example.com,
'@ 
 
$data = $csv | ConvertFrom-Csv

$data.fecha
$data.correo

$data | Out-GridView

```
