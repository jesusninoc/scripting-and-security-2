# Ofuscación en PowerShell
## PowerShell, Security 
### URL: https://www.jesusninoc.com/2017/12/01/ofuscacion-en-powershell/
```PowerShell
####################################################################
#Convertir una cadena de caracteres a binario (Char - Int - Binario)
$resultado = ""
$codificar = 'GC'
foreach($letra in [Char[]]$codificar)
{
$decimal = [Int][Char]$letra
$resultado += [Convert]::ToString($decimal, 2)
}
$resultado
####################################################################

####################################################################
#Convertir una cadena de caracteres a binario (char - int - binario)
([Char[]]"GC" | %{[Convert]::ToString([Int][Char]$_, 2)}) -join ""
####################################################################

####################################################################
#Convertir números en binario en caracteres (agrupando de 7 en 7 bits)
(10001111000011 -split "(?<=\G\d{7})(?=.)" | %{[Char][Convert]::ToInt32($_,2)}) -join ""
####################################################################

####################################################################
#Invertir un script
$valor = '(10001111000011 -split "(?<=\G\d{7})(?=.)" | %{[Char][Convert]::ToInt32($_,2)}) -join ""'
$invertido = $valor[$valor.Length..0]-join ""
$invertido
####################################################################

####################################################################
#Obtener el alias del cmdlet Get-Content mediante Get-Command
(gcm g?)[0].Name
####################################################################

####################################################################
#Obtener el alias del cmdlet Get-Content mediante Get-Command y abrir un fichero
(gcm g?)[0].Name + ' fichero.txt' | Invoke-Expression
####################################################################

```
