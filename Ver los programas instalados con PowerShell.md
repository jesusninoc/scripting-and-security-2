# Ver los programas instalados con PowerShell
## PowerShell, Software 
### URL: https://www.jesusninoc.com/2017/05/30/ver-los-programas-instalados-con-powershell/
```PowerShell
Get-WmiObject -query "select name from win32_product" | select Name

```
