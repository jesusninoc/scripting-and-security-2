# Abrir una cuenta de Twitter y hacer capturas de pantalla de los tuits
## Automation, PowerShell 
### URL: https://www.jesusninoc.com/2016/10/18/abrir-una-cuenta-de-twitter-y-hacer-capturas-de-pantalla-de-los-tuits/
```PowerShell
#Función para capturar pantalla y almacenarla en un fichero
[Reflection.Assembly]::LoadWithPartialName("System.Drawing")
function screenshot($path)
{
$b=New-Object System.Drawing.Bitmap([System.Windows.Forms.Screen]::PrimaryScreen.Bounds.Width, [System.Windows.Forms.Screen]::PrimaryScreen.Bounds.Height)
$g=[System.Drawing.Graphics]::FromImage($b)
$g.CopyFromScreen((New-Object System.Drawing.Point(0,0)), (New-Object System.Drawing.Point(0,0)), $b.Size)
$g.Dispose()
$b.Save($path,'Bmp')
}

#Abrir la cuenta de Twitter
Start-Process chrome https://twitter.com/microsoft

#Hacer captura de pantalla de la cuenta de Twitter, después de realizar la captura avanzar página y volver a realizar la captura de pantalla
$avanzar=0

do
{
Start-Sleep -Seconds 5

$path=’E:\twitter\captura'+$avanzar+'.bmp’
screenshot($path)

#Avanzar página
[System.Windows.Forms.SendKeys]::SendWait("{PGDN}")

$avanzar+=1
}while($avanzar -lt 10)

```
