# Establecer una dirección IPv6 para el interfaz Wi-Fi con PowerShell
## Network, PowerShell 
### URL: https://www.jesusninoc.com/2017/11/03/establecer-una-direccion-ipv6-para-el-interfaz-wi-fi-con-powershell/
```PowerShell
New-NetIPAddress –InterfaceAlias "Wi-Fi" –IPAddress 2001::1

```
