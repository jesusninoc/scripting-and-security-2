# Vínculos simbólicos y vínculos físicos
## Filesystem, PowerShell 
### URL: https://www.jesusninoc.com/2017/11/08/vinculos-simbolicos-y-vinculos-fisicos/
```PowerShell
#Archivo de vínculo simbólico
New-Item -ItemType SymbolicLink -Path E:\powershell -Name ficherolink.txt -Target E:\powershell\ficheros\fichero.txt

#Directorio de vínculo simbólico
New-Item -ItemType SymbolicLink -Path E:\powershell -Name directoriolink -Target E:\powershell\ficheros\

#Vínculo físico
New-Item -ItemType HardLink -Path E:\powershell -Name ficherohardlink.txt -Value E:\powershell\ficheros\fichero.txt

```
