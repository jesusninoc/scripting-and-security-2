# Método GET en PHP desde PowerShell
## PHP, PowerShell 
### URL: https://www.jesusninoc.com/2017/03/04/metodo-get-en-php-desde-powershell/
```PowerShell
###################################################################################################################
#Método GET en PHP desde PowerShell
###################################################################################################################
#Crear el fichero PHP con el contenido:
'<?php echo htmlspecialchars($_GET[''nombre'']) . " tiene " . (int)$_GET[''edad''] . " años." ?>'| out-file scriptphp.php -Encoding utf8 | .\php-cgi.exe -f .\scriptphp.php nombre=Marta edad=20

```
