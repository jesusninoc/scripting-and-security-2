# Crear código QR para una ubicación GPS
## PowerShell 
### URL: https://www.jesusninoc.com/2018/05/27/crear-codigo-qr-para-una-ubicacion-gps/
```PowerShell
# Fichero con el código QR
$path = "ubicacion.png"

# Instalar el módulo QRCodeGenerator
# Automatically creates QR codes as PNG images for persons (vCard), WiFi access, and geo location. Works on all PowerShell versions and editions
Install-Module QRCodeGenerator -Scope CurrentUser -Force

# Crear el código QR
New-QRCodeGeolocation -OutPath $path -Address 'Avenida de Concha Espina 1, Madrid'

```
