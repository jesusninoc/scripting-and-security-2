# Generar HMAC-SHA256 con PowerShell
## PowerShell, Security 
### URL: https://www.jesusninoc.com/2018/02/18/generar-hmac-sha256-con-powershell/
```PowerShell
$hmacsha = New-Object System.Security.Cryptography.HMACSHA256
$hmacsha.key = [Text.Encoding]::ASCII.GetBytes("Clave secreta")
$signature = $hmacsha.ComputeHash([Text.Encoding]::ASCII.GetBytes("Mensaje secreto"))
$signature = [Convert]::ToBase64String($signature)

$signature

```
