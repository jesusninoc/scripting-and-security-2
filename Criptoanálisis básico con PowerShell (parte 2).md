# Criptoanálisis básico con PowerShell (parte 2)
## Cryptography, PowerShell, Security 
### URL: https://www.jesusninoc.com/2017/01/08/criptoanalisis-basico-con-powershell-parte-2/
```PowerShell
Function Combinaciones
{
 Param(
 [Object[]]$Object,
 [String]$Seperator,
 [UInt32]$CurIndex = 0,
 [String]$Return = ""
 )

 $MaxIndex = $Object.Count - 1
 $Object[$CurIndex] | ForEach-Object {
 [Array]$NewReturn = "$($Return)$($Seperator)$($_)".Trim($Seperator)
 If ($CurIndex -lt $MaxIndex) {
 $NewReturn = Combinaciones $Object -CurIndex ($CurIndex + 1) -Return $NewReturn
 }
 $NewReturn
 }
}

#Realizar un criptoanálisis básico para descifrar un texto cifrado por transposición
#Descifrar la cadena yube
$descifrar="yube"

#Añadir un diccionario a una ArrayList para ver si al resolver la transposición se encuentra la palabra en el diccionario
#Inicializa una nueva instancia de la clase ArrayList que está vacía y tiene la capacidad inicial predeterminada
[System.Collections.ArrayList] $arraylist = New-Object System.Collections.ArrayList
ForEach ($elemento in gc .\diccionario.txt){
#Agrega un objeto al final de ArrayList
[void]$arraylist.Add($elemento)
}

$arrayletras=@(0..($descifrar.Length-1) | % {$descifrar[$_]})
$arrayletras

#Combinar cuatro letras distintas en palabras de cuatro letras
#Para cada una de las palabras que se han obtenido comprobar si se encuentra en el diccionario
Combinaciones @($arrayletras,$arrayletras,$arrayletras,$arrayletras) | %{
if($arraylist.IndexOf($_) -eq -1){"Elemento: $_ no encontrado"}
else{"Elemento $_ encontrado en la posición " + $arraylist.IndexOf($_)}
}

```
