# Verificar la ejecución de un comando de Windows desde PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2018/04/20/verificar-la-ejecucion-de-un-comando-de-windows-desde-powershell/
```PowerShell
ping.exe www.jesusninoc.com -n 2 -w 2000
if($LASTEXITCODE -eq 0){"Ping se ha ejecutado correctamente"}

```
