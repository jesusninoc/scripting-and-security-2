# Subir un fichero por SSH a un servidor Linux desde PowerShell en Windows
## PowerShell 
### URL: https://www.jesusninoc.com/2017/11/02/subir-un-fichero-por-ssh-a-un-servidor-linux-desde-powershell-en-windows/
```PowerShell
Set-SCPFile -LocalFile .\index.html -ComputerName 192.168.1.162 -RemotePath . -Credential (Get-Credential)
Invoke-SSHCommand -Index 0 "ls index.html"
Invoke-SSHCommand -Index 0 "ls -la index.html"

```
```PowerShell
(Invoke-SSHCommand -Index 0 "cat index.html").output

```
