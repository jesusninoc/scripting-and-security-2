# Ocultar todos los procesos que se están ejecutando durante unos segundos y después volverlos a mostrar
## PowerShell 
### URL: https://www.jesusninoc.com/2017/10/05/ocultar-todos-los-procesos-que-se-estan-ejecutando-durante-unos-segundos-y-despues-volverlos-a-mostrar/
```PowerShell
#Importar en PowerShell la función que permite cambiar el estado de una ventana de show a hide
$funcion = '[DllImport("user32.dll")] public static extern bool ShowWindowAsync(IntPtr hWnd, int nCmdShow);'
$type = Add-Type -MemberDefinition $funcion -Name myAPI -PassThru
 
#Obtener el identificador del proceso
Get-Process | %{

$process=$_.MainWindowHandle

if($process -ne 0)
{ 
#Obtener el Handle de la ventana que se va a ocultar
$hwnd = $_.MainWindowHandle

#Ocultar la ventana durante 5 segundos llamando a la función ShowWindowAsync con el valor 0
$type::ShowWindowAsync($hwnd, 0)

Start-Sleep -Seconds 5

#Mostra la ventana llamando a la función ShowWindowAsync con el valor 5
$type::ShowWindowAsync($hwnd, 5)
}
}

```
