# Análisis de frecuencias de palabras en un texto con PowerShell (parte 4)
## Cryptography, PowerShell, Security 
### URL: https://www.jesusninoc.com/2017/01/20/analisis-de-frecuencias-de-palabras-en-un-texto-con-powershell-parte-4/
```PowerShell
#Abrir el fichero texto.txt, añadir, agrupar y obtener la frecuencia de cada una de las palabras que contiene el fichero a una ArrayList

#Inicializa una nueva instancia de la clase ArrayList que está vacía y tiene la capacidad inicial predeterminada
[System.Collections.ArrayList] $arraylist = New-Object System.Collections.ArrayList
 
ForEach ($elemento in (gc .\texto.txt).Split(" ")){
#Agrega un objeto al final de ArrayList
[void]$arraylist.Add($elemento)
}

$arraylist | Group-Object | select Name,Count

```
```PowerShell
#Abrir el fichero texto.txt, añadir, agrupar y obtener la frecuencia cada una de las palabras que contiene el fichero a una ArrayList

#Inicializa una nueva instancia de la clase ArrayList que está vacía y tiene la capacidad inicial predeterminada
[System.Collections.ArrayList] $arraylist = New-Object System.Collections.ArrayList
 
ForEach ($elemento in (gc .\texto.txt).Replace(".","").Replace(",","").Split(" ")){
#Agrega un objeto al final de ArrayList
[void]$arraylist.Add($elemento)
}

$arraylist | Group-Object | select Name,Count

```
