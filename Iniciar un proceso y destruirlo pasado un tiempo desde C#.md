# Iniciar un proceso y destruirlo pasado un tiempo desde C#
## C#, Processes 
### URL: https://www.jesusninoc.com/2017/09/30/iniciar-un-proceso-y-destruirlo-pasado-un-tiempo-desde-c/
```C#
using System;
using System.Diagnostics;
using System.Threading;

public class Proceso
{
    public static void Main()
    {

        Process myProcess;
        myProcess = Process.Start(@"C:\Windows\System32\Notepad.exe");

        Thread.Sleep(2000);

        myProcess.Kill();

        // Free resources associated with process.
        myProcess.Close();
    }
}

```
