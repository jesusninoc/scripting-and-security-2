# Ejecutar un cmdlet remotamente en un equipo del dominio
## PowerShell 
### URL: https://www.jesusninoc.com/2017/07/21/ejecutar-un-cmdlet-remotamente-en-un-equipo-del-dominio/
```PowerShell
Invoke-Command -ComputerName servidor {Get-Process}

```
