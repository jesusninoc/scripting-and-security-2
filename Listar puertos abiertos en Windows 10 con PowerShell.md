# Listar puertos abiertos en Windows 10 con PowerShell
## Network, PowerShell 
### URL: https://www.jesusninoc.com/2017/06/28/listar-puertos-abiertos-en-windows-10-con-powershell/
```PowerShell
Get-NetUDPEndpoint | Select-Object LocalPort
Get-NetTCPConnection | Select-Object LocalPort

```
