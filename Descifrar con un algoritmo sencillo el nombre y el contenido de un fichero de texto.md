# Descifrar con un algoritmo sencillo el nombre y el contenido de un fichero de texto
## Cryptography, PowerShell, Security 
### URL: https://www.jesusninoc.com/2017/05/18/descifrar-con-un-algoritmo-sencillo-el-nombre-y-el-contenido-de-un-fichero-de-texto/
```PowerShell
#Fichero cifrado para descifrar
#El fichero se ha cifrado mediante https://www.jesusninoc.com/2017/05/16/cifrar-con-un-algoritmo-sencillo-el-nombre-y-el-contenido-de-un-fichero-de-texto-enviar-la-clave-utilizada-en-el-algoritmo-mediante-una-peticion-web-a-un-servidor/
$fichero="gjdifspuyu"
$cifrado=gc $fichero
$clavecifrado=1
$textodescifrado=(0..($cifrado.Length-1) | % {[char]::ConvertFromUtf32([char]::ConvertToUtf32($cifrado[$_].ToString(),0)-$clavecifrado)}) -join ""

#Descifrar el nombre y el contenido
$ficherocifrado=(0..($fichero.Length-1) | % {[char]::ConvertFromUtf32([char]::ConvertToUtf32($fichero[$_].ToString(),0)-$clavecifrado)}) -join ""
$textodescifrado | Out-File $ficherocifrado

```
