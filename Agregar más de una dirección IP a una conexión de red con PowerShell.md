# Agregar más de una dirección IP a una conexión de red con PowerShell
## Network, PowerShell 
### URL: https://www.jesusninoc.com/2017/02/28/agregar-mas-de-una-direccion-ip-a-una-conexion-de-red-con-powershell/
```PowerShell
foreach($segundo in 1..254)
{
    foreach($tercero in 1..254)
    {
        $ip=("192.168."+$segundo+"."+$tercero)
        $ip
        New-NetIPAddress -InterfaceAlias Wi-Fi -IPAddress $ip -PrefixLength 24
        pause
    }
}

```
