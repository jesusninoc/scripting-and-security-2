# Mostrar información avanzada de los procesos que se están ejecutando en relación con los servicios y los puertos abiertos UDP (Get-NetUDPEndpoint)
## Network, PowerShell, Processes, Services 
### URL: https://www.jesusninoc.com/2017/03/20/mostrar-informacion-avanzada-de-los-procesos-que-se-estan-ejecutando-en-relacion-con-los-servicios-y-los-puertos-abiertos-udp/
```PowerShell
#Mostrar información avanzada de los procesos (Path, ExecutablePath, CommandLine) que se están ejecutando en relación con los servicios y los puertos abiertos UDP
(Get-WmiObject -Class Win32_Service | Where-Object State -EQ 'Running') | %{
#Write-Host $_.Name,$_.ProcessId,$_.State,(Get-Process -Id $_.ProcessId | Select-Object name, Path, ExecutablePath, CommandLine)
Write-Host $_.Name,$_.ProcessId,$_.State,(Get-WmiObject -Class win32_process | Where-Object ProcessId -EQ  $_.ProcessId | select name, Path, ExecutablePath, CommandLine)
Write-Host $_.Name,$_.ProcessId,$_.State,(Get-Process -Id $_.ProcessId).Name,(Get-NetUDPEndpoint | where OwningProcess -EQ $_.ProcessId | select LocalPort,RemoteAddress,RemotePort,OwningProcess)
Write-Host "##################################################"
}

```
