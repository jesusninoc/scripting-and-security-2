# Descargar un fichero por SSH de un servidor Linux desde PowerShell en Windows
## PowerShell 
### URL: https://www.jesusninoc.com/2017/11/04/descargar-un-fichero-por-ssh-de-un-servidor-linux-desde-powershell-en-windows/
```PowerShell
Get-SCPFile -LocalFile fichero.html -RemoteFile index.html -ComputerName 192.168.1.162 -Credential (Get-Credential)

```
