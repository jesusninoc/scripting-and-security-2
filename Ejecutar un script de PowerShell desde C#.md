# Ejecutar un script de PowerShell desde C#
## C#, PowerShell 
### URL: https://www.jesusninoc.com/2017/10/24/ejecutar-un-script-de-powershell-desde-c/
```C#
using System;
using System.Management.Automation;  // Windows PowerShell namespace.

namespace PowerSh
{
    class PowerSh
    {
        static void Main(string[] args)
        {
            PowerShell ps = PowerShell.Create();
            ps.AddScript("gps > procesos.txt");

            IAsyncResult result = ps.BeginInvoke();

            // do something else until execution has completed.
            // this could be sleep/wait, or perhaps some other work
            while (result.IsCompleted == false)
            {
            }

            Console.WriteLine("Fin!");
        } // End Main.
    } // End PowerSh.
}

```
