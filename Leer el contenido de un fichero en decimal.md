# Leer el contenido de un fichero en decimal
## Filesystem, PowerShell 
### URL: https://www.jesusninoc.com/2017/04/20/leer-el-contenido-de-un-fichero-en-decimal/
```PowerShell
Write-Host "Contenido del fichero en decimal"
[System.IO.File]::ReadAllBytes('.\eje.txt')

```
