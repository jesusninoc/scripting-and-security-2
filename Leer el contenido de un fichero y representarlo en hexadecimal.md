# Leer el contenido de un fichero y representarlo en hexadecimal
## Filesystem, PowerShell 
### URL: https://www.jesusninoc.com/2017/02/03/leer-el-contenido-de-un-fichero-y-representarlo-en-hexadecimal/
```PowerShell
#Leer el contenido de un fichero en ASCII
Write-Host "Contenido del fichero en ASCII"
gc .\eje.txt

#Leer el contenido del fichero en decimal
Write-Host "Contenido del fichero en decimal"
[System.IO.File]::ReadAllBytes('.\eje.txt')

#Leer el contenido del fichero en decimal y representar cada símbolo decimal en hexadecimal
Write-Host "Contenido del fichero en hexadecimal"
$val=[System.IO.File]::ReadAllBytes('.\eje.txt')
0..($val.Length-1) | %{
$cadenah=[System.String]::Format("{0:X}", [System.Convert]::ToUInt32($val[$_]))
Write-Host $cadenah
}

```
