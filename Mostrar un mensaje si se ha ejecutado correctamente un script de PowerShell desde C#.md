# Mostrar un mensaje si se ha ejecutado correctamente un script de PowerShell desde C#
## C#, PowerShell 
### URL: https://www.jesusninoc.com/2017/11/07/mostrar-un-mensaje-si-se-ha-ejecutado-correctamente-un-script-de-powershell-desde-c/
```C#
using System;
using System.Collections.ObjectModel;
using System.Management.Automation;  // Windows PowerShell namespace.

namespace PowerSh
{
    class PowerSh
    {
        static void Main(string[] args)
        {
                using (PowerShell PowerShellInstance = PowerShell.Create())
                {
                    // use "AddScript" to add the contents of a script file to the end of the execution pipeline.
                    // use "AddCommand" to add individual commands/cmdlets to the end of the execution pipeline.
                    PowerShellInstance.AddScript("Get-Process | out-file out.txt");

                    Collection<PSObject> PSOutput = PowerShellInstance.Invoke();
                    foreach (PSObject outputItem in PSOutput)
                    {
                        // if null object was dumped to the pipeline during the script then a null
                        // object may be present here. check for null to prevent potential NRE.
                        if (outputItem != null)
                        {
                            Console.WriteLine(outputItem.BaseObject.ToString() + "\n");
                        }
                    }
                if (PowerShellInstance.Streams.Error.Count > 0)
                {
                    Console.Write("Error");
                }
                else
                {
                    Console.Write("Correcto");
                }
                    Console.ReadKey();
                }

        } // End Main.
    } // End PowerSh.
}

```
