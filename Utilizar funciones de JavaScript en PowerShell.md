# Utilizar funciones de JavaScript en PowerShell
## JavaScript, PowerShell 
### URL: https://www.jesusninoc.com/2018/01/05/utilizar-funciones-de-javascript-en-powershell/
```PowerShell
$src = @'
static function hola(arg) {
  var msg = "Hola " + arg;
  Console.WriteLine(msg);
}
'@
$JS = (Add-Type -Language JScript -MemberDefinition $src -Name "JSHola" -PassThru)[1]
$JS::hola((Read-host "Introduzca nombre"))

```
