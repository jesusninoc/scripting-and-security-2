# Die verbundenen Handys auf dem Computer sehen
## PowerShell 
### URL: https://www.jesusninoc.com/2017/02/01/die-verbundenen-handys-auf-dem-computer-sehen/
```PowerShell
Get-PnpDevice | Where-Object { $_.class -EQ 'USBDevice' } | Select-Object FriendlyName

```
