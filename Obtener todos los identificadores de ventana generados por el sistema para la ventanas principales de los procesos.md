# Obtener todos los identificadores de ventana generados por el sistema para la ventanas principales de los procesos
## PowerShell 
### URL: https://www.jesusninoc.com/2016/11/08/obtener-todos-los-identificadores-de-ventana-generados-por-el-sistema-para-la-ventanas-principales-de-los-procesos/
```PowerShell
Get-Process | Select-Object Name,MainWindowHandle

```
