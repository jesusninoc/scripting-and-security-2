# Formas de utilizar el Where en PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2017/04/06/formas-de-utilizar-el-where-en-powershell/
```PowerShell
#Forma 1
$Procesos = Get-Process
$Procesos | Where-Object { $_.Name -eq 'Notepad' }
#Tipo de dato generado
($Procesos | Where-Object { $_.Name -eq 'Notepad' }).GetType()

#Forma 2
$Procesos = Get-Process
$Procesos.Where{ $_.Name -eq 'Notepad' }
#Tipo de dato generado
($Procesos.Where{ $_.Name -eq 'Notepad' }).GetType()

#Forma 3
Get-Process | Where-Object { $_.Name -eq 'Notepad' }
#Tipo de dato generado
(Get-Process | Where-Object { $_.Name -eq 'Notepad' }).GetType()

```
