# Reproducir notas musicales con PowerShell desde C#
## C#, PowerShell 
### URL: https://www.jesusninoc.com/2017/11/05/reproducir-notas-musicales-con-powershell-desde-c/
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
            ps.AddScript("[System.Console]::Beep(261,500);[System.Console]::Beep(293,500);[System.Console]::Beep(329,500);[System.Console]::Beep(349,500);[System.Console]::Beep(391,500);[System.Console]::Beep(440,500);[System.Console]::Beep(493,500)");

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
