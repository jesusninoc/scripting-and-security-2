# Crear código QR para la conexión wifi
## PowerShell 
### URL: https://www.jesusninoc.com/2018/05/23/crear-codigo-qr-para-la-conexion-wifi/
```PowerShell
# Datos de la conexión wifi
$wifi = "RedWifi"
$pwd = "Secreto01passA"
 
# Fichero con el código QR
$path = "wifiaccess.png"
 
# Instalar el módulo QRCodeGenerator
# Automatically creates QR codes as PNG images for persons (vCard), WiFi access, and geo location. Works on all PowerShell versions and editions
Install-Module QRCodeGenerator -Scope CurrentUser -Force

# Crear el código QR
New-QRCodeWifiAccess -SSID $wifi -Password $pwd -OutPath $path

```
