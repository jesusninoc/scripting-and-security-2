# Abrir Firefox en modo privado desde PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2018/03/11/abrir-firefox-en-modo-privado-desde-powershell/
```PowerShell
[System.Diagnostics.Process]::Start("firefox.exe","-private-window $url")

```
