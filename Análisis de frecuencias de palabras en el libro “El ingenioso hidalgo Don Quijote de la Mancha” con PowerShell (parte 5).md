# Análisis de frecuencias de palabras en el libro “El ingenioso hidalgo Don Quijote de la Mancha” con PowerShell (parte 5)
## Cryptography, PowerShell, Security 
### URL: https://www.jesusninoc.com/2017/01/22/analisis-de-frecuencias-de-palabras-en-el-libro-el-ingenioso-hidalgo-don-quijote-de-la-mancha-con-powershell-parte-5/
```PowerShell
#Abrir el fichero texto.txt, añadir, agrupar y obtener la frecuencia de cada una de las palabras que contiene el fichero a una ArrayList

#Inicializa una nueva instancia de la clase ArrayList que está vacía y tiene la capacidad inicial predeterminada
[System.Collections.ArrayList] $arraylist = New-Object System.Collections.ArrayList

ForEach ($elemento in (gc .\quijote.txt).Split(" ")){
#Agrega un objeto al final de ArrayList
[void]$arraylist.Add($elemento)
}

$arraylist | Group-Object | Sort-Object Count -Descending | select Name,Count

```
