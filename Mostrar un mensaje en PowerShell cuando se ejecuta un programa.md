# Mostrar un mensaje en PowerShell cuando se ejecuta un programa
## PowerShell 
### URL: https://www.jesusninoc.com/2017/09/04/mostrar-un-mensaje-en-powershell-cuando-se-ejecuta-un-programa/
```PowerShell
#Arrancar programa notepad.exe y no avisa con mensaje que se ha ejecutado
Start-Process notepad.exe

#Registrar la acción de avisar cuando se ejecuta el programa notepad.exe
#La clase WMI del evento Win32_ProcessStartTrace indica que se ha iniciado un nuevo proceso.
Register-WMIEvent -Query "SELECT * FROM Win32_ProcessStartTrace WHERE ProcessName='notepad.exe'" -Action {Write-Host "Nuevo proceso notepad"} 

#Arrancar programa notepad.exe y avisa con mensaje que se ha ejecutado
Start-Process notepad.exe

```
