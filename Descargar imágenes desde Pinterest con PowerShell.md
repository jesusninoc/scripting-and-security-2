# Descargar imágenes desde Pinterest con PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2017/02/21/descargar-imagenes-desde-pinterest-con-powershell/
```PowerShell
Start-Process chrome https://es.pinterest.com/microsoft/you-inspire-us/
$web=Invoke-WebRequest https://es.pinterest.com/microsoft/you-inspire-us/
Start-Sleep -Seconds 5
$web.Images.src | %{Start-BitsTransfer $_}

```
