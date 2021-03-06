# Introducción a la automatización en PowerShell
## Automation, PowerShell 
### URL: https://www.jesusninoc.com/2017/03/06/introduccion-a-la-automatizacion-en-powershell/
```PowerShell
#Ejercicio 1
#Posición X,Y
$dX = ([System.Windows.Forms.Cursor]::Position.X) #Coordenada X
$dY = ([System.Windows.Forms.Cursor]::Position.Y) #Coordenada Y
$dX,$dY

#Ejercicio 2
#Ver la posición X,Y de forma indefinida cada medio segundo
for ()
{
Start-Sleep -m 500
$dX = ([System.Windows.Forms.Cursor]::Position.X)
$dY = ([System.Windows.Forms.Cursor]::Position.Y)
Write-Host $dX,$dY #print
}

#Ejercicio 3
#Almacenar las posiciones en un fichero
for (1)
{
Start-Sleep -s 1
$dX = ([System.Windows.Forms.Cursor]::Position.X)
$dY = ([System.Windows.Forms.Cursor]::Position.Y)
Write-Host $dX,$dY
$dX.ToString()+','+$dY.ToString() | Out-File posicion.txt -Append
}

#Ejercicio 4
#Reproducir las posiciones almacenadas en un fichero
gc .\posicion.txt | %{
Start-Sleep -s 1
[System.Windows.Forms.Cursor]::Position = New-Object System.Drawing.Point($_.split(',')[0],$_.split(',')[1])
}

#Ejercicio 5
#Hacer clic izquierdo en una posición de la pantalla
#Funciones y declaraciones necesarias para poder hacer clic 
$MouseEventSig=@’
[DllImport("user32.dll",CharSet=CharSet.Auto, CallingConvention=CallingConvention.StdCall)]
public static extern void mouse_event(long dwFlags, long dx, long dy, long cButtons, long dwExtraInfo);
‘@
$MouseEvent = Add-Type -memberDefinition $MouseEventSig -name “MouseEventWinApi” -passThru
#Hacer clic izquierdo en el botón de inicio
[System.Windows.Forms.Cursor]::Position = New-Object System.Drawing.Point(19,741)
$MouseEvent::mouse_event(0x00000002, 0, 0, 0, 0);
$MouseEvent::mouse_event(0x00000004, 0, 0, 0, 0);

#Ejercicio 6
#Hacer clic derecho en una posición de la pantalla
#Funciones y declaraciones necesarias para poder hacer clic 
$MouseEventSig=@’
[DllImport("user32.dll",CharSet=CharSet.Auto, CallingConvention=CallingConvention.StdCall)]
public static extern void mouse_event(long dwFlags, long dx, long dy, long cButtons, long dwExtraInfo);
‘@
$MouseEvent = Add-Type -memberDefinition $MouseEventSig -name “MouseEventWinApi” -passThru
#Hacer clic derecho en el botón de inicio
[System.Windows.Forms.Cursor]::Position = New-Object System.Drawing.Point(19,741)
$MouseEvent::mouse_event(0x00000008, 0, 0, 0, 0);
$MouseEvent::mouse_event(0x00000010, 0, 0, 0, 0);

#Ejercicio 7
#Pintar una línea automáticamente en Paint
#Desde la posición 200,200 a la posición 300,300
Start-Process C:\WINDOWS\system32\mspaint.exe
Start-Sleep -Seconds 5
[System.Windows.Forms.Cursor]::Position = New-Object System.Drawing.Point(200,200)
$MouseEvent::mouse_event(0x00000002, 0, 0, 0, 0)
Start-Sleep -Seconds 2
[System.Windows.Forms.Cursor]::Position = New-Object System.Drawing.Point(300,300)
$MouseEvent::mouse_event(0x00000004, 0, 0, 0, 0)

```
