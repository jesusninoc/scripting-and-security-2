# Devolver un número especificado de elementos desde el inicio de una secuencia utilizando LINQ en PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2017/09/25/devolver-un-numero-especificado-de-elementos-desde-el-inicio-de-una-secuencia-utilizando-linq-en-powershell/
```PowerShell
[int[]] $numeros = @(1,2,3,4,5,6)
[Linq.Enumerable]::Take($numeros,3)

```
