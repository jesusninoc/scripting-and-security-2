# How to find Windows uptime
## Network, PowerShell 
### URL: https://www.jesusninoc.com/2017/07/24/how-to-find-windows-uptime/
```PowerShell
net statistics server | Select-String "stics since"
net statistics server | Select-String "sticas desde"

```
