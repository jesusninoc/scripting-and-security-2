# Crear y ejecutar un script de PowerShell en Linux realizando una conexión SSH desde PowerShell en Windows
## PowerShell 
### URL: https://www.jesusninoc.com/2017/10/27/crear-y-ejecutar-un-script-de-powershell-en-linux-realizando-una-conexion-ssh-desde-powershell-en-windows/
```PowerShell
New-SSHSession -ComputerName 192.168.1.162 -Credential (Get-Credential)
Invoke-SSHCommand -Index 0 'echo "echo hola" > script2.ps1'
Invoke-SSHCommand -Index 0 "cat script2.ps1"
Invoke-SSHCommand -Index 0 "powershell script2.ps1"

```
