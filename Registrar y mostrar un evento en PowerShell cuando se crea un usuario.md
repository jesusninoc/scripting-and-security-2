# Registrar y mostrar un evento en PowerShell cuando se crea un usuario
## PowerShell 
### URL: https://www.jesusninoc.com/2018/02/16/registrar-y-mostrar-un-evento-en-powershell-cuando-se-crea-un-usuario/
```PowerShell
#Ejecutar PowerShell como administrador
Register-WmiEvent -Query "select * from __InstanceCreationEvent where TargetInstance isa 'Win32_NtLogEvent' and TargetInstance.logfile = 'Security' and (TargetInstance.EventCode = '4720')" -Action {Write-Host $event.SourceEventArgs.NewEvent.TargetInstance.insertionstrings}

```
