# Análisis de frecuencias de letras en un texto con PowerShell (parte 2)
## Cryptography, PowerShell, Security 
### URL: https://www.jesusninoc.com/2017/01/12/analisis-de-frecuencias-de-letras-en-un-texto-con-powershell-parte-2/
```PowerShell
#Abrir el fichero texto.txt, añadir y agrupar cada una de las letras que contiene el fichero en una ArrayList

#Inicializa una nueva instancia de la clase ArrayList que está vacía y tiene la capacidad inicial predeterminada
[System.Collections.ArrayList] $arraylist = New-Object System.Collections.ArrayList
 
ForEach ($elemento in [char[]](gc .\texto.txt)){
#Agrega un objeto al final de ArrayList
[void]$arraylist.Add($elemento)
}

$arraylist | Group-Object

```
