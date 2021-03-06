# Rundll32 commands for Windows
## Filesystem, Hardware, Network, Users 
### URL: https://www.jesusninoc.com/2017/04/12/rundll32-commands-for-windows/
```PowerShell
# Control Panel
RunDll32.exe shell32.dll,Control_RunDLL

# Delete Temporary Internet Files
RunDll32.exe InetCpl.cpl,ClearMyTracksByProcess 8

# Delete Cookies
RunDll32.exe InetCpl.cpl,ClearMyTracksByProcess 2

# Delete History
RunDll32.exe InetCpl.cpl,ClearMyTracksByProcess 1

# Delete Form Data
RunDll32.exe InetCpl.cpl,ClearMyTracksByProcess 16

# Delete Passwords
RunDll32.exe InetCpl.cpl,ClearMyTracksByProcess 32

# Delete All
RunDll32.exe InetCpl.cpl,ClearMyTracksByProcess 255

# Delete all files and settings stored by Add-ons
RunDll32.exe InetCpl.cpl,ClearMyTracksByProcess 4351

# Date and Time Properties
RunDll32.exe shell32.dll,Control_RunDLL timedate.cpl

# Device Manager
RunDll32.exe devmgr.dll DeviceManager_Execute

# Folder Options – General
RunDll32.exe shell32.dll,Options_RunDLL 0

# Folder Options – Search
RunDll32.exe shell32.dll,Options_RunDLL 2

# Folder Options – View
RunDll32.exe shell32.dll,Options_RunDLL 7

# Hibernate
RunDll32.exe powrprof.dll,SetSuspendState

# Keyboard Properties
RunDll32.exe shell32.dll,Control_RunDLL main.cpl @1

# Lock Screen
RunDll32.exe user32.dll,LockWorkStation

# Mouse Button – Swap left button to function as right
Rundll32 User32.dll,SwapMouseButton

# Map Network Drive Wizard
Rundll32 Shell32.dll,SHHelpShortcuts_RunDLL Connect

# Network Connections
RunDll32.exe shell32.dll,Control_RunDLL ncpa.cpl

# Organize IE Favourites
Rundll32.exe shdocvw.dll,DoOrganizeFavDlg

# Open With Dialog Box
Rundll32 Shell32.dll,OpenAs_RunDLL File.ext

# Plays a waveform sound
rundll32.exe user32.dll,MessageBeep

# Printer User Interface
Rundll32 Printui.dll,PrintUIEntry

# Printer Management Folder.
Rundll32 Shell32.dll,SHHelpShortcuts_RunDLL PrintersFolder

# Power Options
RunDll32.exe Shell32.dll,Control_RunDLL powercfg.cpl

# Stored Usernames and Passwords
RunDll32.exe keymgr.dll,KRShowKeyMgr

# Safely Remove Hardware Dialog Box
Rundll32 Shell32.dll,Control_RunDLL HotPlug.dll

# Taskbar Properties
RunDll32.exe shell32.dll,Options_RunDLL 1

# User Accounts
RunDll32.exe shell32.dll,Control_RunDLL nusrmgr.cpl

# Windows Security Center
RunDll32.exe shell32.dll,Control_RunDLL wscui.cpl

# Windows Fonts Installation Folder
Rundll32 Shell32.dll,SHHelpShortcuts_RunDLL FontsFolder

# Windows Firewall
RunDll32.exe shell32.dll,Control_RunDLL firewall.cpl

# Abrir la calculadora
rundll32 zipfldr.dll, RouteTheCall calc.exe
rundll32 advpack.dll, RegisterOCX calc.exe
rundll32 c:\Windows\System32\pcwutl.dll,LaunchApplication calc.exe

# You looking out for that "RegisterOCX" function in IEAdvpack.dll?  
rundll32.exe C:\windows\system32\IEAdvpack.dll,RegisterOCX C:\path\to\payload.dll
rundll32.exe C:\windows\system32\IEAdvpack.dll,RegisterOCX C:\path\to\payload.exe
rundll32.exe IEAdvpack.dll,RegisterOCX calc.exe

# Llame al Asistente de conexión de la unidad de red
rundll32.exe shell32.dll, SHHelpShortcuts_RunDLL Connect

# Abra un cuadro de diálogo que muestra la versión del sistema operativo Windows. También puede mostrar este cuadro de diálogo ejecutando el comando winver.exe
rundll32.exe shell32.dll, ShellAboutA

# Muestra el árbol del sistema de archivos del disco duro de la computadora
rundll32.exe IEAKENG.dll, BrowseForFileA

# Llame al cuadro de diálogo AYUDA Y SOPORTE en la página especificada. Por ejemplo, puede usar la llamada mshelp como la página html: // Windows /? Id = 33307acf-0698-41ba-b014-ea0a2eb8d0a8
rundll32.exe ndfapi.dll, NdfRunDllHelpTopic "html-page"

# Llame al diálogo ABRIR COMO ... para abrir este archivo
rundll32.exe shell32.dll, OpenAs_RunDLL "ruta y nombre de archivo"

# Muestra el cuadro de diálogo de la utilidad de red del cliente de SQL Server
rundll32.exe shell32.dll, Control_RunDLL Cliconfg.dll

# Muestra el cuadro de diálogo Eliminar dispositivo
rundll32.exe shell32.dll, Control_RunDLL Hotplug.dll

# Reescribe el contenido de este archivo
rundll32.exe admparse.dll, CheckDuplicateKeysA "ruta y nombre de archivo"

# Crea una carpeta. Si esta carpeta ya existe, se borrarán todos sus contenidos
rundll32.exe IEAKENG.dll, BToolbar_SaveA "ruta a la carpeta"

# Inicia el navegador de Internet Explorer y descarga la página http://g.msn.com/WMHFUSEN/101724
rundll32.exe appwiz.cpl, GetProgramsOnline

# Ejecuta el comando
rundll32.exe shell32.dll, ShellExec_RunDLL "comando"

# Abra la carpeta. Si no especifica una carpeta, se abrirá la carpeta de su perfil
rundll32.exe url.dll, FileProtocolHandler "directorio"

# Elimina todos los archivos de la carpeta especificada que tienen el atributo FILEATTRIBUTETAGINFORMATION
rundll32.exe WININET.dll, RunOnceUrlCache "ruta a la carpeta"

# Ejecute el archivo xml
rundll32.exe xwizards.dll, ProcessXMLFile "ruta y nombre del archivo xml"

# Presiona el botón derecho del mouse
rundll32.exe user32.dll, mouse_event

# Coloque el cursor en la esquina inferior derecha de la pantalla
rundll32.exe user32.dll, SetCursorPos

# Detener el servicio de actualización en segundo plano dfsvc.exe
rundll32.exe dfshim.dll, KillService

# Ejecuta los comandos descritos en la rama de registro HKLM \ SOFTWARE \ Microsoft \ Windows \ CurrentVersion \ RunOnceEx (o en la rama de la partición raíz HKCU)
rundll32.exe IERNONCE.dll, RunOnceExProcess

```
