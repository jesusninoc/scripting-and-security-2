# Relación entre puertos TCP, procesos y lista de puertos de la IANA (junto con una breve descripción de cada puerto)
## Network, PowerShell 
### URL: https://www.jesusninoc.com/2016/12/30/relacion-entre-puertos-tcp-procesos-y-lista-de-puertos-de-la-iana-junto-con-una-breve-descripcion-de-cada-puerto/
```PowerShell
#Descargar y guardar el listado de puertos
Invoke-WebRequest 'https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.csv' -OutFile e:\service-names-port-numbers.csv

#Relación entre puertos abiertos TCP y lista de puertos la IANA
$portscsv=Import-Csv e:\service-names-port-numbers.csv
$listado=$portscsv | Select-Object 'Service Name','Port Number','Transport Protocol','Description' | Where-Object 'Transport Protocol' -EQ tcp
Get-NetTCPConnection | %{Write-Host $_.Localaddress, ($listado | Select-Object 'Service Name','Port Number','Description' | Where-Object 'Port Number' -EQ $_.RemotePort), $_.Remoteaddress} | Format-Custom

```
