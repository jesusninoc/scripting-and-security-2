# Crear un usuario local con contraseña en Windows 10 con PowerShell 5.1
## PowerShell, Users 
### URL: https://www.jesusninoc.com/2016/11/23/crear-un-usuario-local-con-contrasena-en-windows-10-con-powershell-5-1/
```PowerShell
$pass=ConvertTo-SecureString "11234aaa@@€dsf" -asplaintext -force; 
New-LocalUser usuario -Password $pass

```
