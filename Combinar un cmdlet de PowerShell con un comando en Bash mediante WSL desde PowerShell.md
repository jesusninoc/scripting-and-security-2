# Combinar un cmdlet de PowerShell con un comando en Bash mediante WSL desde PowerShell
## Bash, PowerShell 
### URL: https://www.jesusninoc.com/2018/05/31/combinar-un-cmdlet-de-powershell-con-un-comando-en-bash-mediante-wsl-desde-powershell/
```PowerShell
# Opción 1
powershell.exe Write-Host hola | wsl wc -c

# Opción 2
"hola" | bash -c 'wc -c'

```
