# Registrar y mostrar un evento en PowerShell cuando se ejecuta un programa
## PowerShell 
### URL: https://www.jesusninoc.com/2018/02/14/registrar-y-mostrar-un-evento-en-powershell-cuando-se-ejecuta-un-programa/
```PowerShell
#Ejecutar PowerShell como administrador
while(1)
{
Get-Event | Remove-Event -ErrorAction SilentlyContinue
#Registrar el evento de ejecutar notepad
Register-WmiEvent -Query "SELECT * FROM Win32_ProcessStartTrace"
Wait-Event -OutVariable Event | Out-Null
$Event
}

```
