# Ejecutar en PowerShell mediante ofuscación y Expresiones Regulares
## Obfuscation, PowerShell, Security 
### URL: https://www.jesusninoc.com/2018/06/24/ejecutar-en-powershell-mediante-ofuscacion-y-expresiones-regulares/
```PowerShell
# Ejecutar el cmdlet Write-Host (muestra un texto en PowerShell)
.(get-alias i`*X)("Write-Host texto")
.(get-alias `i*****?X)("Write-Host texto")
.((get-alias ??X)[1])("Write-Host texto")
.(get-alias [eri][teg][xcv])("Write-Host texto")

# Ejecutar el cmdlet Write-Host (muestra un texto en PowerShell) mediante el alias de Get-Alias
.(alias i`*X)("Write-Host texto")

# Ejecutar el cmdlet Get-Process (muestra los procesos que se están ejecutando en PowerShell)
.(alias [eri][teg][xcv])("Write-Host texto")

# Ejecutar el cmdlet Invoke-WebRequest (enviar una petición HTTP o HTTPS a un servidor web)
(.(alias i`*r)("https://www.jesusninoc.com"))

```
