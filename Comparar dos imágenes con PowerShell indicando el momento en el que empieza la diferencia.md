# Comparar dos imágenes con PowerShell indicando el momento en el que empieza la diferencia
## Graphics, PowerShell 
### URL: https://www.jesusninoc.com/2018/01/30/comparar-dos-imagenes-con-powershell-indicando-el-momento-en-el-que-empieza-la-diferencia/
```PowerShell
#Es necesario que las dos imágenes estén en la misma posición inicial
$foto1 = [System.Drawing.Bitmap]::FromFile('C:\Users\juan\Desktop\recono\coche.png')
$foto2 = [System.Drawing.Bitmap]::FromFile('C:\Users\juan\Desktop\recono\coche - copia.png')

$pixelestotales=0
$pixelesdistintos=0

$primeraposicion=0

for($y=0;$y -lt $foto1.Height;$y+=1)
{
    for($x=0;$x -lt $foto1.Width;$x+=1)
    {
        $pixelestotales+=1
        if($foto1.GetPixel($x,$y).name -eq $foto2.GetPixel($x,$y).name)
        {
        }
        else
        {
            $pixelesdistintos+=1
            if($primeraposicion -eq 0)
            {
                Write-Host "Empieza la diferencia de la foto: $x,$y"
                $primeraposicion=1
            }
        }
    }
}

$porcentajepixelesdistintos=($pixelesdistintos/$pixelestotales)*100
Write-Host "Píxeles totales: $pixelestotales"
Write-Host "Píxeles distintos: $pixelesdistintos, porcentaje de píxeles distintos: $porcentajepixelesdistintos"

```
