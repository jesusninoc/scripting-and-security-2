# Comprobar la versión de Linux mips que corre en el router de fibra óptica MitraStar GPT-2541GNAC de Movistar desde PowerShell
## Network, PowerShell 
### URL: https://www.jesusninoc.com/2018/03/26/comprobar-la-version-de-linux-mips-que-corre-en-el-router-de-fibra-optica-mitrastar-gpt-2541gnac-de-movistar-desde-powershell/
```PowerShell
New-SSHSession -ComputerName 192.168.1.1 -Credential (Get-Credential)
Get-SSHSession
(Invoke-SSHCommand -Index 0 "/var/bin2/uname").output
(Invoke-SSHCommand -Index 0 "/var/bin2/uname -a").output

```
