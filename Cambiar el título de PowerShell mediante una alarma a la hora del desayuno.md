# Cambiar el título de PowerShell mediante una alarma a la hora del desayuno
## PowerShell 
### URL: https://www.jesusninoc.com/2017/07/28/cambiar-el-titulo-de-powershell-mediante-una-alarma-a-la-hora-del-desayuno/
```PowerShell
$code =
{
    # Enviar la interfaz RawUI del proceso host y el contexto de ejecución
    param($RawUi)
    do
    {
        $HoraActual = Get-Date -Format 'HH:mm'
        $HoraAlarma = Get-Date -Format 'HH:mm' -Hour 10 -Minute 00
        if($HoraActual -eq $HoraAlarma){
                # Cambiar título
                $RawUI.WindowTitle = "Es hora de desayunar"
        }
        else
        {
                $RawUI.WindowTitle = "Es hora de trabajar"
        }

        # Esperar medio segundo
        Start-Sleep -Milliseconds 500
    }while ($true)
}

$ps = [PowerShell]::Create()
$null = $ps.AddScript($code).AddArgument($host.UI.RawUI)
$handle = $ps.BeginInvoke()

```
