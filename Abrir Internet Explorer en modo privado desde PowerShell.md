# Abrir Internet Explorer en modo privado desde PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2018/03/13/abrir-internet-explorer-en-modo-privado-desde-powershell/
```PowerShell
[System.Diagnostics.Process]::Start("iexplore.exe","$url -private")

```
