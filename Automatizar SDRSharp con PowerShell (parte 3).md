# Automatizar SDRSharp con PowerShell (parte 3)
## PowerShell, Radio 
### URL: https://www.jesusninoc.com/2017/03/15/automatizar-sdrsharp-con-powershell-parte-3/
```PowerShell
#Abrir SDRSharp
Start-Process E:\sdrsharp-x86\SDRSharp.exe

Start-Sleep -Seconds 5

#Funciones necesarias para hacer clic
$MouseEventSig=@'
[DllImport("user32.dll",CharSet=CharSet.Auto, CallingConvention=CallingConvention.StdCall)]
public static extern void mouse_event(long dwFlags, long dx, long dy, long cButtons, long dwExtraInfo);
'@
$MouseEvent = Add-Type -memberDefinition $MouseEventSig -name "MouseEventWinApi" -passThru

#Hacer clic en el botón del menú para ocultarlo
[System.Windows.Forms.Cursor]::Position = New-Object System.Drawing.Point(23,54)
$MouseEvent::mouse_event(0x00000002, 0, 0, 0, 0)
$MouseEvent::mouse_event(0x00000004, 0, 0, 0, 0)

Start-Sleep -Seconds 5

#Hacer clic en Start para poner en funcionamiento SDRSharp
[System.Windows.Forms.Cursor]::Position = New-Object System.Drawing.Point(60,54)
$MouseEvent::mouse_event(0x00000002, 0, 0, 0, 0)
$MouseEvent::mouse_event(0x00000004, 0, 0, 0, 0)

Start-Sleep -Seconds 5

#Mover el cursor hasta la posición de los MHz y hacer clic
[System.Windows.Forms.Cursor]::Position = New-Object System.Drawing.Point(382,54)
$MouseEvent::mouse_event(0x00000002, 0, 0, 0, 0)
$MouseEvent::mouse_event(0x00000004, 0, 0, 0, 0)

Start-Sleep -Seconds 5

#Escribir en la posición de los MHz el valor 400
[System.Windows.Forms.SendKeys]::SendWait("400")

```
