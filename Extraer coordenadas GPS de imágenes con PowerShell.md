# Extraer coordenadas GPS de imágenes con PowerShell
## Graphics, PowerShell 
### URL: https://www.jesusninoc.com/2018/01/01/extraer-coordenadas-gps-de-imagenes-con-powershell/
```PowerShell
$imagePath = 'C:\Users\juan\Desktop\recono\IMG_20171226_232738.jpg'
$imageProperties = New-Object -TypeName System.Drawing.Bitmap -ArgumentList $imagePath

[double]$LatDegrees = (([System.BitConverter]::ToInt32( $imageProperties.GetPropertyItem(2).Value, 0)) / ([System.BitConverter]::ToInt32( $imageProperties.GetPropertyItem(2).Value, 4)));
[double]$LatMinutes = ([System.BitConverter]::ToInt32( $imageProperties.GetPropertyItem(2).Value, 8)) / ([System.BitConverter]::ToInt32( $imageProperties.GetPropertyItem(2).Value, 12));
[double]$LatSeconds = ([System.BitConverter]::ToInt32( $imageProperties.GetPropertyItem(2).Value, 16)) / ([System.BitConverter]::ToInt32( $imageProperties.GetPropertyItem(2).Value, 20));
[double]$LonDegrees = (([System.BitConverter]::ToInt32( $imageProperties.GetPropertyItem(4).Value, 0)) / ([System.BitConverter]::ToInt32( $imageProperties.GetPropertyItem(4).Value, 4)));
[double]$LonMinutes = ([System.BitConverter]::ToInt32( $imageProperties.GetPropertyItem(4).Value, 8)) / ([System.BitConverter]::ToInt32( $imageProperties.GetPropertyItem(4).Value, 12));
[double]$LonSeconds = ([System.BitConverter]::ToInt32( $imageProperties.GetPropertyItem(4).Value, 16)) / ([System.BitConverter]::ToInt32( $imageProperties.GetPropertyItem(4).Value, 20));

"Latitude: $LatDegrees;$LatMinutes;$LatSeconds"
"Longitude: $LonDegrees;$LonMinutes;$LonSeconds"

```
