# Analizar información de red (protocolo UDP)
## Network, PowerShell 
### URL: https://www.jesusninoc.com/2017/04/28/analizar-informacion-de-red-protocolo-udp/
```PowerShell
#Relación puertos y procesos
Get-NetUDPEndpoint | %{Write-Host $_.LocalAddress,$_.LocalPort,$_.RemotePort,$_.OwningProcess,(Get-Process -id $_.OwningProcess).Name}

```
