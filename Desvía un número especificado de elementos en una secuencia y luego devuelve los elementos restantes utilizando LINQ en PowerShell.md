# Desvía un número especificado de elementos en una secuencia y luego devuelve los elementos restantes utilizando LINQ en PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2017/09/27/desvia-un-numero-especificado-de-elementos-en-una-secuencia-y-luego-devuelve-los-elementos-restantes-utilizando-linq-en-powershell/
```PowerShell
[int[]] $numeros = @(1,2,3,4,5,6)
[Linq.Enumerable]::Skip($numeros,3)

```
