# Conocer la relevancia de una búsqueda en Google
## PowerShell 
### URL: https://www.jesusninoc.com/2016/12/10/conocer-la-relevancia-de-una-busqueda-en-google/
```PowerShell
$urls='https://www.google.com/search?q=powershell'
$result=Invoke-WebRequest $urls
$valor=($result.AllElements | ? {$_.id -eq “resultStats”}).innerText
$valor=$valor.replace("Aproximadamente","").replace("resultados","").replace(".","")
$valor=$valor.Trim()
switch([Int]$valor)
{
{$_ -ge 0 -and $_ -le 1000}{"Poco importante"}
{$_ -ge 1001 -and $_ -le 10000}{"Algo importante"}
{$_ -ge 10000 -and $_ -le 100000000}{"Muy importante"}
}

```
