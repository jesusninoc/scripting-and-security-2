# PHP en PowerShell con ejemplos
## PHP, PowerShell 
### URL: https://www.jesusninoc.com/2017/02/20/php-en-powershell-con-ejemplos/
```PowerShell
#Ir a la capeta donde se encuentra PHP
cd C:\xampp\php

###################################################################################################################
#Variables 1: enteros, caracteres y cadenas de caracteres
###################################################################################################################
#Crear tipos de datos: enteros, caracteres y cadenas de caracteres
#Forma 1
'<?php $num = 5;
echo "$num\n";
$car=''c'';
echo "$car\n";
$cad=''$hola'';
echo "$cad\n";?>' | .\php.exe
#Forma 2
'<?php $num = 5;
echo "$num\n";
$car="c";
echo "$car\n";
$cad="hola";
echo "$cad\n";?>' | .\php.exe
#Código en una línea
'<?php $num = 5;echo "$num\n";$car=''c'';echo "$car\n";$cad=''hola'';echo "$cad\n";?>' | .\php.exe
#Almacenar en un fichero codificando en UTF-8
'<?php $num = 5;echo "$num\n";$car=''c'';echo "$car\n";$cad=''hola'';echo "$cad\n";?>' | out-file scriptphp.php -Encoding utf8 | .\php.exe scriptphp.php

```
```PowerShell
#Ir a la capeta donde se encuentra PHP
cd C:\xampp\php

###################################################################################################################
#Variables 2: concatenar, extraer elementos y medir la longitud de un array
###################################################################################################################
#Concatenar una cadena
'<?php $palabra1 = "hola";
$palabra2 = "adios"; 
echo $palabra1 ." " . $palabra2;?>' | .\php.exe
#Código en una línea
'<?php $palabra1 = "hola"; $palabra2 = "adios"; echo $palabra1 ." " . $palabra2;?>' | .\php.exe

#Extraer elementos de una cadena
'<?php $hola="Hola Mundo"; echo $hola[0]; ?>' | .\php.exe
'<?php $hola="Hola Mundo"; echo $hola[1]; ?>' | .\php.exe

#Medir la longitud de un array
'<?php $hola="Hola Mundo"; echo strlen($hola); ?>' | .\php.exe

#Número de palabras en un array
'<?php $hola="Hola Mundo"; echo str_word_count($hola); ?>' | .\php.exe

```
