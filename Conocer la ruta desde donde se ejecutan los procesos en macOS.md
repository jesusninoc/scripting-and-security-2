# Conocer la ruta desde donde se ejecutan los procesos en macOS
## PowerShell, Processes 
### URL: https://www.jesusninoc.com/2016/10/11/conocer-la-ruta-desde-donde-se-ejecutan-los-procesos-en-macos/
```PowerShell
Get-Process | Select-Object Name,Path

```
```Shell
ps x

```
