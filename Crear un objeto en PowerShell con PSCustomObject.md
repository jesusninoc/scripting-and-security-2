# Crear un objeto en PowerShell con PSCustomObject
## PowerShell 
### URL: https://www.jesusninoc.com/2017/08/31/crear-un-objeto-en-powershell-con-pscustomobject/
```PowerShell
$CustomObject = [PSCustomObject]@{Marca="Audi";Modelo="A3";Color="rojo"}
$CustomObject | Format-List

```
