# Ver el SID (Security Identifier) de un usuario en Windows con PowerShell
## PowerShell, Users 
### URL: https://www.jesusninoc.com/2017/08/28/ver-el-sid-security-identifier-de-un-usuario-en-windows-con-powershell/
```PowerShell
$objUser = New-Object System.Security.Principal.NTAccount("juan")
$SID = $objUser.Translate([System.Security.Principal.SecurityIdentifier])
$SID.Value

```
