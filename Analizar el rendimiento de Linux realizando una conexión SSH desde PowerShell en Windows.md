# Analizar el rendimiento de Linux realizando una conexión SSH desde PowerShell en Windows
## Bash, Memory, Operating Systems, PowerShell, Processes 
### URL: https://www.jesusninoc.com/2017/10/28/analizar-el-rendimiento-de-linux-realizando-una-conexion-ssh-desde-powershell-en-windows/
```PowerShell
New-SSHSession -ComputerName 192.168.1.162 -Credential (Get-Credential)

#analizar.txt:
#uptime
#dmesg
#vmstat
#mpstat -P ALL
#pidstat
#iostat -xz
#free -m
#sar -n DEV
#sar -n TCP,ETCP
#ps

gc analizar.txt | %{
$_
$resultado=Invoke-SSHCommand -Index 0 $_
"---------------------------------------------------------------" | Out-File resultado.txt -Append
$resultado.Output | Out-File resultado.txt -Append
Start-Sleep -Seconds 5
}

```
