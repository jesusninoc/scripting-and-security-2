# Tareas programadas en PowerShell
## PowerShell, Schedule tasks 
### URL: https://www.jesusninoc.com/2017/03/01/tareas-programadas-en-powershell/
```PowerShell
#Crear una tarea programada
#Crear una acción
$action=New-ScheduledTaskAction -Execute 'notepad.exe'
#Crear el activador
$trigger=New-ScheduledTaskTrigger -Daily -At 16:25pm
#Registrar la tarea programada
Register-ScheduledTask -Action $action -Trigger $trigger -TaskName "Tarea Programada" -Description "Abrir Notepad"

#Deshabilitar una tarea programada
Disable-ScheduledTask -TaskName "Tarea Programada"

#Activar una tarea programada
Enable-ScheduledTask -TaskName "Tarea Programada"

#Anular el registro de una tarea programada
Unregister-ScheduledTask -TaskName "Tarea Programada"

#Ver todas las tareas programadas
Get-ScheduledTask

```
