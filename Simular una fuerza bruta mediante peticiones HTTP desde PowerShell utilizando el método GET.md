# Simular una fuerza bruta mediante peticiones HTTP desde PowerShell utilizando el método GET
## PHP, PowerShell 
### URL: https://www.jesusninoc.com/2018/04/01/simular-una-fuerza-bruta-mediante-peticiones-http-desde-powershell-utilizando-el-metodo-get/
```PowerShell
cd C:\xampp\php

'<?PHP
$usuario = "pedro";
$pass= "123456";
if(! (htmlspecialchars($_GET["username"]) == $usuario && htmlspecialchars($_GET["password"]) == $pass) ){
    echo "<html>";
    echo "<title>MUY mal</title>";
    echo "<b>Acceso denegado</b>";        
    return false;
}
else {
    echo "<html>";
    echo "<title>MUY bien</title>";
    echo "<b>Acceso concedido</b>";
    return true;
}
?>'| out-file scriptphp.php -Encoding utf8

.\php-cgi.exe -f .\scriptphp.php username=pepito password=1234
.\php-cgi.exe -f .\scriptphp.php username=pedro password=123456

```
