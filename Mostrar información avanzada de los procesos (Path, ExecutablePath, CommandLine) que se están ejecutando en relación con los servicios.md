# Mostrar información avanzada de los procesos (Path, ExecutablePath, CommandLine) que se están ejecutando en relación con los servicios
## PowerShell, Processes, Services 
### URL: https://www.jesusninoc.com/2016/11/12/mostrar-informacion-avanzada-de-los-procesos-path-executablepath-commandline-que-se-estan-ejecutando-en-relacion-con-los-servicios/
```PowerShell
#Mostrar información avanzada de los procesos (Path, ExecutablePath, CommandLine) que se están ejecutando en relación con los servicios
(Get-WmiObject -Class Win32_Service | Where-Object State -EQ 'Running') | %{
#Write-Host $_.Name,$_.ProcessId,$_.State,(Get-Process -Id $_.ProcessId | Select-Object name, Path, ExecutablePath, CommandLine)
Write-Host $_.Name,$_.ProcessId,$_.State,(Get-WmiObject -Class win32_process | Where-Object ProcessId -EQ  $_.ProcessId | select name, Path, ExecutablePath, CommandLine)
Write-Host "##################################################"
}

```
