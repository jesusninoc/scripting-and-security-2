# Mostrar las coordenadas del mouse con PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2017/11/17/mostrar-las-coordenadas-del-mouse-con-powershell/
```PowerShell
while(1){Start-Sleep -m 500;Write-Host ([System.Windows.Forms.Cursor]::Position | Select-Object X,Y)}

```
