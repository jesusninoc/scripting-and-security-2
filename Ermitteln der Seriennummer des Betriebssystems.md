# Ermitteln der Seriennummer des Betriebssystems
## Hardware, PowerShell 
### URL: https://www.jesusninoc.com/2017/02/24/ermitteln-der-seriennummer-des-betriebssystems/
```PowerShell
Get-WmiObject -query "select SerialNumber from Win32_OperatingSystem"

```
