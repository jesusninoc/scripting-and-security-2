# Recuperar un identificador de una ventana generado por el sistema para la ventana principal del proceso Notepad y escribir un texto en el proceso
## PowerShell 
### URL: https://www.jesusninoc.com/2016/11/17/recuperar-un-identificador-de-una-ventana-generado-por-el-sistema-para-la-ventana-principal-del-proceso-notepad-y-escribir-un-texto-en-el-proceso/
```PowerShell
#La función FindWindowEx
#Recupera un identificador a una ventana cuyo nombre de clase y nombre de la ventana que coincida con las cadenas especificadas. La función busca en ventanas secundarias, comenzando por la raíz de la ventana secundaria especificada. Esta función no realiza una búsqueda entre mayúsculas y minúsculas.
#La función SendMessage
#Envía el mensaje especificado a una ventana o ventanas. La función SendMessage llama al procedimiento de ventana de la ventana especificada y no vuelve hasta que el procedimiento de ventana ha procesado el mensaje.

$codigo='
[DllImport("user32.dll", EntryPoint = "FindWindowEx")]public static extern IntPtr FindWindowEx(IntPtr hwndParent, IntPtr hwndChildAfter, string lpszClass, string lpszWindow);
[DllImport("User32.dll")]public static extern int SendMessage(IntPtr hWnd, int uMsg, int wParam, string lParam);
'

$acciones=Add-Type -MemberDefinition $codigo -Name TextoNotepad -PassThru

[IntPtr]$acciones::FindWindowEx((Get-Process Notepad | Select-Object Name,MainWindowHandle).MainWindowHandle, [IntPtr]::Zero, "Edit", $null)

$acciones::SendMessage([IntPtr]$acciones::FindWindowEx((Get-Process Notepad | Select-Object Name,MainWindowHandle).MainWindowHandle, [IntPtr]::Zero, "Edit", $null), 0x000C, 0, "Texto")

```
