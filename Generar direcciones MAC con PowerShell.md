# Generar direcciones MAC con PowerShell
## Network, PowerShell 
### URL: https://www.jesusninoc.com/2017/08/30/generar-direcciones-mac-con-powershell/
```PowerShell
(0..5 | ForEach-Object { '{0:x}{1:x}' -f (Get-Random -Minimum 0 -Maximum 15),(Get-Random -Minimum 0 -Maximum 15)})  -join ':'

```
