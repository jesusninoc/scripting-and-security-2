# Crear y extraer un password de tipo SecureString
## Cryptography, PowerShell, Security 
### URL: https://www.jesusninoc.com/2017/02/26/crear-y-extraer-un-password-de-tipo-securestring/
```PowerShell
#Crear password de tipo SecureString
$SecurePassword = Read-Host -Prompt "Introduzca password" -AsSecureString

#Extraer password de tipo SecureString
$BSTR = [System.Runtime.InteropServices.Marshal]::SecureStringToBSTR($SecurePassword)
$PlainPassword = [System.Runtime.InteropServices.Marshal]::PtrToStringAuto($BSTR)

$PlainPassword

```
