# Cifrar con un algoritmo sencillo el nombre y el contenido de un fichero de texto
## Cryptography, PowerShell, Security 
### URL: https://www.jesusninoc.com/2017/01/23/cifrar-con-un-algoritmo-sencillo-el-nombre-y-el-contenido-de-un-fichero-de-texto/
```PowerShell
ForEach($fichero in ls .)
{
#Cifrar el contenido del fichero
$cifrado=gc $fichero
$var=1
$textocifrado=(0..($cifrado.Length-1) | % {[char]::ConvertFromUtf32([char]::ConvertToUtf32($cifrado[$_].ToString(),0)+$var)}) -join ""

#Cifrar el nombre y añadir el contenido cifrado
#Quitamos los puntos y otros caracteres para no tener errores a la hora de crear el nuevo fichero cifrado
$ficherosin=$fichero.Name.Replace(".","")
$ficherosin
$ficherocifrado=(0..($ficherosin.Length-1) | % {[char]::ConvertFromUtf32([char]::ConvertToUtf32($ficherosin[$_].ToString(),0)+$var)}) -join ""
$textocifrado | Out-File $ficherocifrado
}

```
