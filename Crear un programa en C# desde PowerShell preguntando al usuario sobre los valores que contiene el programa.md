# Crear un programa en C# desde PowerShell preguntando al usuario sobre los valores que contiene el programa
## C#, PowerShell 
### URL: https://www.jesusninoc.com/2017/10/02/crear-un-programa-en-c-desde-powershell-preguntando-al-usuario-sobre-los-valores-que-contiene-el-programa/
```PowerShell
$pediruser=Read-Host "Valor que pasar a C#"

$Codigo = @"

namespace Ejemplo
{
public class Ejemplo
{
public static void Main()
{
System.Console.WriteLine("$pediruser");
}
}
}

"@

Add-Type -TypeDefinition $Codigo

[Ejemplo.Ejemplo]::Main()

```
