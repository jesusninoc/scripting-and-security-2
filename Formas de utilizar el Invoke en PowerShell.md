# Formas de utilizar el Invoke en PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2017/04/09/formas-de-utilizar-el-invoke-en-powershell/
```PowerShell
#Forma 1
$Procesos = {Get-Process}
& $Procesos
#Tipo de dato generado
(& $Procesos).GetType().FullName

#Forma 2
$Procesos = {Get-Process}
$Procesos.Invoke()
#Tipo de dato generado
$Procesos.Invoke().GetType().FullName

```
