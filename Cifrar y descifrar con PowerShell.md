# Cifrar y descifrar con PowerShell
## PowerShell, Security 
### URL: https://www.jesusninoc.com/2017/01/03/cifrar-y-descifrar-con-powershell/
```PowerShell
#####################################
#FORMA 1
#INCREMENTAR 2
#####################################

#Cifrar incrementando 2 a cada letra
$text="abcdefghij abcd"
$var=2
(0..($text.Length-1) | % {[char]::ConvertFromUtf32([char]::ConvertToUtf32($text[$_].ToString(),0)+$var)}) -join ""

#Descifrar decrementando 2 a cada letra
$textC='cdefghijkl"cdef'
$varC=2
(0..($textC.Length-1) | % {[char]::ConvertFromUtf32([char]::ConvertToUtf32($textC[$_].ToString(),0)-$varC)}) -join ""

#####################################
#FORMA 2
#INCREMENTAR VALOR A CADA POSICIÓN
#####################################

#Cifrar incrementando un valor a cada letra (el valor empieza en 0 y va sumando 1)
$text="abcdefghij abcd"
$var=0
(0..($text.Length-1) | % {[char]::ConvertFromUtf32([char]::ConvertToUtf32($text[$_].ToString(),0)+($var=$var+1))}) -join ""

#Descifrar decrementando un valor a cada letra (el valor empieza en 0 y va restando 1)
$textC="bdfhjlnprt+moqs"
$varC=0
(0..($textC.Length-1) | % {[char]::ConvertFromUtf32([char]::ConvertToUtf32($textC[$_].ToString(),0)+($varC=$varC-1))}) -join ""

#####################################
#FORMA 3
#POSICIONES PARES
#####################################

#Cifrar las posiciones pares de una frase
$text="abcdefghij abcd"
$var=0
(0..($text.Length-1) | % {
if($var%2){([char]::ConvertFromUtf32([char]::ConvertToUtf32($text[$_].ToString(),0)+1))}else{[char]::ConvertFromUtf32([char]::ConvertToUtf32($text[$_].ToString(),0)+$valorono)}
$var=$var+1}) -join ""

#Descifrar las posiciones pares de una frase
$textC="acceeggiik bbdd"
$varC=0
(0..($textC.Length-1) | % {
if($varC%2){([char]::ConvertFromUtf32([char]::ConvertToUtf32($textC[$_].ToString(),0)-1))}else{[char]::ConvertFromUtf32([char]::ConvertToUtf32($textC[$_].ToString(),0)+$valoronoC)}
$varC=$varC+1}) -join ""

```
