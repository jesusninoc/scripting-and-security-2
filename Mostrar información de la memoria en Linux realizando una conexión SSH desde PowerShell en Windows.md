# Mostrar información de la memoria en Linux realizando una conexión SSH desde PowerShell en Windows
## Bash, Memory, PowerShell 
### URL: https://www.jesusninoc.com/2017/10/05/mostrar-informacion-de-la-memoria-en-linux-realizando-una-conexion-ssh-desde-powershell-en-windows/
```PowerShell
New-SSHSession -ComputerName 192.168.1.162 -Credential (Get-Credential)
$resultado=Invoke-SSHCommand -Index 0 'cat /proc/meminfo'
$resultado.Output

```
