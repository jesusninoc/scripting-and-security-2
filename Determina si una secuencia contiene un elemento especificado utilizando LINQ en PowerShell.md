# Determina si una secuencia contiene un elemento especificado utilizando LINQ en PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2017/09/29/determina-si-una-secuencia-contiene-un-elemento-especificado-utilizando-linq-en-powershell/
```PowerShell
[String[]] $StringData = @("uno", "dos", "tres")
[Linq.Enumerable]::Contains($StringData, "dos")

```
