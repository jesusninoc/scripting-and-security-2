# Recuperar un identificador de una ventana generado por el sistema para la ventana principal del proceso Notepad
## PowerShell, Processes 
### URL: https://www.jesusninoc.com/2016/11/14/recuperar-un-identificador-de-una-ventana-generado-por-el-sistema-para-la-ventana-principal-del-proceso-notepad/
```PowerShell
#La función FindWindowEx
#Recupera un identificador a una ventana cuyo nombre de clase y nombre de la ventana que coincida con las cadenas especificadas. La función busca en ventanas secundarias, comenzando por la raíz de la ventana secundaria especificada. Esta función no realiza una búsqueda entre mayúsculas y minúsculas.

$codigo='
[DllImport("user32.dll", EntryPoint = "FindWindowEx")]public static extern IntPtr FindWindowEx(IntPtr hwndParent, IntPtr hwndChildAfter, string lpszClass, string lpszWindow);
'

$acciones=Add-Type -MemberDefinition $codigo -Name TextoNotepad -PassThru

[IntPtr]$acciones::FindWindowEx((Get-Process Notepad | Select-Object Name,MainWindowHandle).MainWindowHandle, [IntPtr]::Zero, "Edit", $null)

```
