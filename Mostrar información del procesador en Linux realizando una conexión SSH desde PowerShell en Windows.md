# Mostrar información del procesador en Linux realizando una conexión SSH desde PowerShell en Windows
## PowerShell 
### URL: https://www.jesusninoc.com/2017/10/02/mostrar-informacion-del-procesador-en-linux-realizando-una-conexion-ssh-desde-powershell-en-windows/
```PowerShell
New-SSHSession -ComputerName 192.168.1.162 -Credential (Get-Credential)
$resultado=Invoke-SSHCommand -Index 0 'cat /proc/cpuinfo'
$resultado.Output

```
