# Mostrar los procesos que se están ejecutando en relación con los servicios y los puertos abiertos TCP
## Network, PowerShell, Processes, Services 
### URL: https://www.jesusninoc.com/2017/03/12/mostrar-los-procesos-que-se-estan-ejecutando-en-relacion-con-los-servicios-y-los-puertos-abiertos-tcp/
```PowerShell
#Mostrar los procesos que se están ejecutando en relación con los servicios y los puertos abiertos TCP
(Get-WmiObject -Class Win32_Service | Where-Object State -EQ 'Running') | %{
Write-Host $_.Name,$_.ProcessId,$_.State,(Get-Process -Id $_.ProcessId).Name,(Get-NetTCPConnection | where OwningProcess -EQ $_.ProcessId | select LocalPort,RemoteAddress,RemotePort,OwningProcess)
}

```
