# Registrar un evento y mostrar un mensaje en PowerShell cuando se ejecutan varios programas
## PowerShell, Security 
### URL: https://www.jesusninoc.com/2017/10/29/registrar-un-evento-y-mostrar-un-mensaje-en-powershell-cuando-se-ejecutan-varios-programas/
```PowerShell
#Ejecutar PowerShell como administrador
while(1)
{
Get-Event | Remove-Event -ErrorAction SilentlyContinue
#Registrar el evento de ejecutar notepad
Register-WmiEvent -Query "SELECT * FROM Win32_ProcessStartTrace WHERE ProcessName='notepad.exe' or ProcessName='chrome.exe'"
Wait-Event -OutVariable Event | Out-Null
$Event.sourceargs.newevent | select-Object ProcessName,TIME_CREATED
}

```
