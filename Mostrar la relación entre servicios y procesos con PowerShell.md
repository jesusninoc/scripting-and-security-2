# Mostrar la relación entre servicios y procesos con PowerShell
## PowerShell, Processes, Services 
### URL: https://www.jesusninoc.com/2017/10/11/mostrar-la-relacion-entre-servicios-y-procesos-con-powershell/
```PowerShell
Get-WmiObject -Class Win32_Service | Select-Object Name,@{Name="ProcessID";Expression={$_.ProcessID;(Get-Process -Id $_.ProcessID).name}}

```
