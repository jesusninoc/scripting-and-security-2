# Obtener información sobre los dispositivos USB conectados en un equipo del dominio con PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2017/07/23/obtener-informacion-sobre-los-dispositivos-usb-conectados-en-un-equipo-del-dominio-con-powershell/
```PowerShell
Invoke-Command -ComputerName equipo1 {Get-ItemProperty -Path 'Registry::HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Enum\USBSTOR\*\*\'}

```
