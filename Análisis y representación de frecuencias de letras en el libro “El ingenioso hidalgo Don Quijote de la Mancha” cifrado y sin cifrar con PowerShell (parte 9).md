# Análisis y representación de frecuencias de letras en el libro “El ingenioso hidalgo Don Quijote de la Mancha” cifrado y sin cifrar con PowerShell (parte 9)
## Cryptography, PowerShell, Security 
### URL: https://www.jesusninoc.com/2017/02/02/analisis-y-representacion-de-frecuencias-de-letras-en-el-libro-el-ingenioso-hidalgo-don-quijote-de-la-mancha-cifrado-y-sin-cifrar-con-powershell-parte-9/
```PowerShell
#Abrir el fichero quijote.txt, añadir a una ArrayList, agrupar y obtener la frecuencia cada una de las letras que contiene el fichero

#Inicializa una nueva instancia de la clase ArrayList que está vacía y tiene la capacidad inicial predeterminada
[System.Collections.ArrayList] $arraylist = New-Object System.Collections.ArrayList
 
ForEach ($elemento in gc .\quijote.txt){
#Agrega un objeto al final de ArrayList
0..($elemento.Length-1) | %{
[void]$arraylist.Add($elemento[$_])
}
}

#Representar la frecuencia gráficamente
$arraylist | Group-Object | Sort-Object Count -Descending | select Name,Count | %{
$frecuencia=([math]::truncate(($_.count/$arraylist.Count)*100))
$frecuenciadibujo=((1..$frecuencia) | %{Write-Host '█' -NoNewline})
Write-Host $_.name,$frecuencia,$frecuenciadibujo
}

```
```PowerShell
#Abrir el fichero quijotecif.txt, añadir a una ArrayList, agrupar y obtener la frecuencia cada una de las letras que contiene el fichero

#Inicializa una nueva instancia de la clase ArrayList que está vacía y tiene la capacidad inicial predeterminada
[System.Collections.ArrayList] $arraylist = New-Object System.Collections.ArrayList
 
ForEach ($elemento in gc .\quijotecif.txt){
#Agrega un objeto al final de ArrayList
0..($elemento.Length-1) | %{
[void]$arraylist.Add($elemento[$_])
}
}

#Representar la frecuencia gráficamente
$arraylist | Group-Object | Sort-Object Count -Descending | select Name,Count | %{
$frecuencia=([math]::truncate(($_.count/$arraylist.Count)*100))
$frecuenciadibujo=((1..$frecuencia) | %{Write-Host '█' -NoNewline})
Write-Host $_.name,$frecuencia,$frecuenciadibujo
}

```
