# Downloading RTLSDR Driver with PowerShell
## PowerShell, Radio 
### URL: https://www.jesusninoc.com/2017/01/27/downloading-rtlsdr-driver-with-powershell/
```PowerShell
Write-Host "Downloading RTLSDR Driver"
Start-BitsTransfer https://osmocom.org/attachments/download/2242/RelWithDebInfo.zip
Expand-Archive .\RelWithDebInfo.zip

```
