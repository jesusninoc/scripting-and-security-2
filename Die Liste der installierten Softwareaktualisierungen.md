# Die Liste der installierten Softwareaktualisierungen
## PowerShell, Software, Updates 
### URL: https://www.jesusninoc.com/2017/01/18/die-liste-der-installierten-softwareaktualisierungen/
```PowerShell
#Die Liste der installierten Softwareaktualisierungen
Get-HotFix
Get-Package | ? {$_.ProviderName -eq 'msu'}

```
