# SSH desde PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2017/09/24/ssh-desde-powershell/
```PowerShell
Import-Module Posh-SSH

```
```PowerShell
New-SSHSession -ComputerName 192.168.1.161 -Credential (Get-Credential)

```
```PowerShell
Get-SSHSession
Invoke-SSHCommand -Index 0 "uname"

```
