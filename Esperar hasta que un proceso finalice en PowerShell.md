# Esperar hasta que un proceso finalice en PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2017/03/17/esperar-hasta-que-un-proceso-finalice-en-powershell/
```PowerShell
Start-Process notepad
while (Get-Process -Name notepad -ErrorAction SilentlyContinue)
{Start-Sleep -Seconds 1}

```
