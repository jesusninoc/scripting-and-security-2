# Mostrar los títulos en color de los procesos que se están ejecutando en Windows con PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2018/04/08/mostrar-los-titulos-en-color-de-los-procesos-que-se-estan-ejecutando-en-windows-con-powershell/
```PowerShell
$ColorMainWindowTitle = @{
    Name = "MainWindowTitle"
    Expression =
    {
        switch ($_.MainWindowTitle)
        {
            default    { $color = "255;0;255" }
        }
        $esc = [char]27
        "$esc[38;2;${color}m$($_.Name)${esc}[0m"
    }
}

Get-Process | Where {$_.MainWindowTitle} | Select-Object ProcessName, $ColorMainWindowTitle

```
