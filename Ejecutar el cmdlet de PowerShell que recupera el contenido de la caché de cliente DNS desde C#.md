# Ejecutar el cmdlet de PowerShell que recupera el contenido de la caché de cliente DNS desde C#
## C#, Network, PowerShell 
### URL: https://www.jesusninoc.com/2017/10/12/ejecutar-el-cmdlet-de-powershell-que-recupera-el-contenido-de-la-cache-de-cliente-dns-desde-c/
```C#
using System;
using System.Management.Automation;  // Windows PowerShell namespace.

namespace HostPS1
{
    class HostPS1
    {
        static void Main(string[] args)
        {

            // Call the PowerShell.Create() method to create an 
            // empty pipeline.
            PowerShell ps = PowerShell.Create();

            // Call the PowerShell.AddCommand(string) method.
            ps.AddCommand("Get-DnsClientCache");

            Console.WriteLine("Entry                 Data");
            Console.WriteLine("----------------------------");


            // Call the PowerShell.Invoke() method to run the 
            // commands of the pipeline in the default runspace.
            foreach (PSObject result in ps.Invoke())
            {
                Console.WriteLine("{0,-24}{1}",
                        result.Members["Entry"].Value,
                        result.Members["Data"].Value);
            } // End foreach.
        } // End Main.
    } // End HostPs1.
}

```
