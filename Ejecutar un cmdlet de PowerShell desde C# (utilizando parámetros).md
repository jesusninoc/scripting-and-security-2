# Ejecutar un cmdlet de PowerShell desde C# (utilizando parámetros)
## C#, PowerShell 
### URL: https://www.jesusninoc.com/2017/08/25/ejecutar-un-cmdlet-de-powershell-desde-c-utilizando-parametros/
```C#
using System;
using System.Management.Automation;  // Windows PowerShell namespace.

namespace PowerSh
{
    class PowerSh

    {
        static void Main(string[] args)
        {

            //Create a PowerShell object.
            PowerShell ps = PowerShell.Create();
            //Add the command that you want to execute.
            ps.AddCommand("Get-Process");
            //Add the parameter
            ps.AddParameter("Name", "Notepad");
            //Add the command that you want to execute.
            ps.AddCommand("out-file");
            //Add the argument
            ps.AddArgument("out.txt");
            //Invoke the command.
            ps.Invoke();

        } // End Main.
    } // End PowerSh.
}

```
