# Conocer la relevancia de varias búsquedas en Google
## PowerShell 
### URL: https://www.jesusninoc.com/2017/07/02/conocer-la-relevancia-de-varias-busquedas-en-google/
```PowerShell
#Leer nombres en un fichero para realizar la búsqueda en Google, crear el fichero con los términos de búsqueda
Get-Content .\nombres.txt | %{ 
$urls='https://www.google.com/search?q='+ $_ +''
$result=Invoke-WebRequest $urls
$valor=($result.AllElements | ? {$_.id -eq “resultStats”}).innerText
$valor=$valor.replace("Aproximadamente","")
$valor=$valor.replace("resultados","")
$valor=$valor.Trim()
Write-Host $_
Write-Host $valor
}

```
