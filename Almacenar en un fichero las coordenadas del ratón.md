# Almacenar en un fichero las coordenadas del ratón
## Automation, PowerShell, Security 
### URL: https://www.jesusninoc.com/2017/01/16/almacenar-en-un-fichero-las-coordenadas-del-raton/
```PowerShell
for (1)
{
Start-Sleep -s 2
$dY = ([System.Windows.Forms.Cursor]::Position.Y)
$dX = ([System.Windows.Forms.Cursor]::Position.X)
Write-Host $dX,$dY
$dX.ToString()+','+$dY.ToString() | Out-File posicion.txt -Append
}

```
