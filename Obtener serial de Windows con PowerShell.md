# Obtener serial de Windows con PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2017/12/02/obtener-serial-de-windows-con-powershell/
```PowerShell
(Get-WmiObject -query ‘select * from SoftwareLicensingService’).OA3xOriginalProductKey

```
