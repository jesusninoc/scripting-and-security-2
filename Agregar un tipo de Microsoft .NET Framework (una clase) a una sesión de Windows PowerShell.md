# Agregar un tipo de Microsoft .NET Framework (una clase) a una sesión de Windows PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2017/09/01/agregar-un-tipo-de-microsoft-net-framework-una-clase-a-una-sesion-de-windows-powershell/
```PowerShell
$CodigoC2 = @”

using System;

public class Clase
{
public static void Main()
{
Console.WriteLine("Ejemplo función agregada");
}
}

“@

Add-Type -TypeDefinition $CodigoC2 -ErrorAction SilentlyContinue

[Clase]::Main()

```
