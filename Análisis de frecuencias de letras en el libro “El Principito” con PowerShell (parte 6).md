# Análisis de frecuencias de letras en el libro “El Principito” con PowerShell (parte 6)
## Cryptography, PowerShell, Security 
### URL: https://www.jesusninoc.com/2017/07/21/analisis-de-frecuencias-de-letras-en-el-libro-el-principito-con-powershell-parte-6/
```PowerShell
#Abrir el fichero principito.txt, añadir a una ArrayList, agrupar y obtener la frecuencia de cada una de las letras que contiene el fichero

#Inicializa una nueva instancia de la clase ArrayList que está vacía y tiene la capacidad inicial predeterminada
[System.Collections.ArrayList] $arraylist = New-Object System.Collections.ArrayList
 
ForEach ($elemento in gc .\principito.txt){
#Agrega un objeto al final de ArrayList
0..($elemento.Length-1) | %{
[void]$arraylist.Add($elemento[$_])
}
}

$arraylist | Group-Object | Sort-Object Count -Descending | select Name,Count

```
