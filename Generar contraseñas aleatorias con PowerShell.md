# Generar contraseñas aleatorias con PowerShell
## PowerShell, Security 
### URL: https://www.jesusninoc.com/2017/05/31/generar-contrasenas-aleatorias-con-powershell/
```PowerShell
Add-Type -AssemblyName System.Web
$Longitud = 12
$Caracteres = 3
[System.Web.Security.Membership]::GeneratePassword($Longitud, $Caracteres)

```
