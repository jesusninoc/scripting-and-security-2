# Obtener información sobre el hardware creando un objeto con todos los datos
## Hardware, PowerShell 
### URL: https://www.jesusninoc.com/2017/09/07/obtener-informacion-sobre-el-hardware-creando-un-objeto-con-todos-los-datos/
```PowerShell
#Llamadas WMI
$ComputerSystem=Get-WmiObject Win32_ComputerSystem
$BaseBoard=Get-WmiObject Win32_BaseBoard
$BIOS=Get-WmiObject Win32_BIOS
$Processor=Get-WmiObject Win32_Processor
$Battery=Get-WmiObject Win32_Battery
 
#Crear un objeto con todos los datos sobre el hardware
[PSCustomObject]@{
 Model = $ComputerSystem.Model
 ManufacturerBoard = $BaseBoard.Manufacturer
 BIOSVersion = $BIOS.SMbiosbiosversion
 BIOSSerialNumber = $BIOS.serialnumber
 ManufacturerProcessor=$Processor.Manufacturer
 MaxClockSpeed=$Processor.MaxClockSpeed
 DeviceIDBattery=$Battery.DeviceID.trim()
}

```
