# Localizar geográficamente una IP
## Network, PowerShell 
### URL: https://www.jesusninoc.com/2017/04/02/localizar-geograficamente-una-ip/
```PowerShell
$ip = "8.8.8.8"
Invoke-RestMethod -Uri "https://geoip.nekudo.com/api/$ip" | Select-Object -ExpandProperty Country

```
