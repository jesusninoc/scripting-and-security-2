# Ejecutar un código de C# desde PowerShell que ejecuta un cmdlet de PowerShell
## C#, PowerShell 
### URL: https://www.jesusninoc.com/2017/10/14/ejecutar-un-codigo-de-c-desde-powershell-que-ejecuta-un-cmdlet-de-powershell/
```C#
$CodigoC = @”

using System;
using System.Management.Automation;  // Windows PowerShell namespace.

namespace HostPS1
{
    public class HostPS1
    {
        public static void Main()
        {

            // Call the PowerShell.Create() method to create an 
            // empty pipeline.
            PowerShell ps = PowerShell.Create();

            ps.AddCommand("Get-WmiObject");
            ps.AddArgument("win32_physicalmemory");
            ps.AddCommand("sort-object");
            ps.AddArgument("Manufacturer");

            // Call the PowerShell.Invoke() method to run the 
            // commands of the pipeline in the default runspace.
            foreach (PSObject result in ps.Invoke())
            {
                Console.WriteLine(result.Members["Manufacturer"].Value);
            } // End foreach.
        } // End Main.
    } // End HostPs1.
}

“@

Add-Type -TypeDefinition $CodigoC -ErrorAction SilentlyContinue

[HostPS1.HostPS1]::Main()

```
