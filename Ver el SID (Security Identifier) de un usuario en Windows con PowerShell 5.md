# Ver el SID (Security Identifier) de un usuario en Windows con PowerShell 5
## PowerShell, Users 
### URL: https://www.jesusninoc.com/2018/02/04/ver-el-sid-security-identifier-de-un-usuario-en-windows-con-powershell-5/
```PowerShell
Get-LocalUser | Select-Object -Property Name, Sid

```
