# Leer el contenido de un fichero en ASCII y representarlo en decimal
## PowerShell 
### URL: https://www.jesusninoc.com/2017/01/29/leer-el-contenido-de-un-fichero-en-ascii-y-representarlo-en-decimal/
```PowerShell
#Leer el contenido de un fichero en ASCII
Write-Host "Contenido del fichero en ASCII"
gc .\eje.txt

#Leer el contenido del fichero en decimal
Write-Host "Contenido del fichero en decimal"
[System.IO.File]::ReadAllBytes('.\eje.txt')

#Leer el contenido del fichero en decimal y representar cada símbolo decimal en decimal
Write-Host "Cada símbolo que hay en el fichero se representa en decimal"
[System.Text.Encoding]::ASCII.getBytes([System.IO.File]::ReadAllBytes('.\eje.txt'))

#Cada símbolo se representa en decimal
[System.IO.File]::ReadAllBytes('.\eje.txt') | %{
Write-Host "Símbolo:"$_ "se representa en decimal:" ([System.Text.Encoding]::ASCII.getBytes($_))
}

```
