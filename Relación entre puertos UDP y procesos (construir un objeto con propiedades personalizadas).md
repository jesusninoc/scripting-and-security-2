# Relación entre puertos UDP y procesos (construir un objeto con propiedades personalizadas)
## Network, PowerShell 
### URL: https://www.jesusninoc.com/2018/05/02/relacion-entre-puertos-udp-y-procesos-construir-un-objeto-con-propiedades-personalizadas/
```PowerShell
Get-NetUDPEndpoint | Select-Object LocalAddress,LocalPort,OwningProcess,@{n='Nombre proceso';e={Get-Process -id ($_ | Select-Object -ExpandProperty OwningProcess) | Select-Object -ExpandProperty Name}}

```
