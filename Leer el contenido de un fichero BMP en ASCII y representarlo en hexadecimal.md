# Leer el contenido de un fichero BMP en ASCII y representarlo en hexadecimal
## Filesystem, PowerShell 
### URL: https://www.jesusninoc.com/2017/04/22/leer-el-contenido-de-un-fichero-bmp-en-ascii-y-representarlo-en-hexadecimal/
```PowerShell
#Leer el contenido de un fichero en ASCII
Write-Host "Contenido del fichero BMP blanco en ASCII"
gc .\blanco.bmp
Write-Host "Contenido del fichero BMP negro en ASCII"
gc .\negro.bmp

#Leer el contenido del fichero BMP blanco en decimal y representar cada símbolo decimal en hexadecimal
Write-Host "Contenido del fichero BMP blanco en hexadecimal"
$val=[System.IO.File]::ReadAllBytes('.\blanco.bmp')
0..($val.Length-1) | %{
$cadenah=[System.String]::Format("{0:X}", [System.Convert]::ToUInt32($val[$_]))
Write-Host $cadenah " " -NoNewline
}
Write-Host ""

#Leer el contenido del fichero BMP blanco en decimal y representar cada símbolo decimal en hexadecimal
Write-Host "Contenido del fichero BMP negro en hexadecimal"
$val=[System.IO.File]::ReadAllBytes('.\negro.bmp')
0..($val.Length-1) | %{
$cadenah=[System.String]::Format("{0:X}", [System.Convert]::ToUInt32($val[$_]))
Write-Host $cadenah " " -NoNewline
}

```
