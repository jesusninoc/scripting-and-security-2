# Almacenar y utilizar credenciales mediante JSON
## PowerShell, Security 
### URL: https://www.jesusninoc.com/2017/04/08/almacenar-y-utilizar-credenciales-mediante-json/
```PowerShell
#Almacenar credenciales en un fichero JSON
Get-Credential | Select Username,@{n="Password"; e={$_.password | ConvertFrom-SecureString}} | ConvertTo-Json | Set-Content -Path credenciales.json -Encoding UTF8
notepad .\credenciales.json

#Utilizar credenciales desde un fichero JSON
$jsonc = Get-Content -Path .\credenciales.json -Encoding UTF8 -Raw | ConvertFrom-Json
$cred = New-Object -TypeName PSCredential $jsonc.UserName,($jsonc.Password | ConvertTo-SecureString)
Start-Process notepad -Credential $cred

```
