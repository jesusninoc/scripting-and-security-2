# Dispositivos conectados (Plug and Play) en el sistema operativo
## Hardware, PowerShell 
### URL: https://www.jesusninoc.com/2016/11/30/dispositivos-conectados-plug-and-play-en-el-sistema-operativo/
```PowerShell
Get-PnpDevice | Select-Object FriendlyName,InstanceId | Sort-Object FriendlyName

```
