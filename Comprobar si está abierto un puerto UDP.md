# Comprobar si está abierto un puerto UDP
## Network, PowerShell 
### URL: https://www.jesusninoc.com/2018/03/01/comprobar-si-esta-abierto-un-puerto-udp/
```PowerShell
while(1)
{
Get-NetUDPEndpoint | Select-Object LocalAddress,LocalPort | Where-Object {$_.LocalPort -eq "5353"}
Start-Sleep -Seconds 5
clear
}

```
