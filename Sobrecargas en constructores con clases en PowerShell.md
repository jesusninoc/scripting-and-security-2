# Sobrecargas en constructores con clases en PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2017/08/01/sobrecargas-en-constructores-con-clases-en-powershell/
```PowerShell
class Coche
{
    [string]$Marca
    [string]$Modelo
 
    #Constructor 1
    Coche([string]$Marca, [string]$Modelo)
    {
        $this.Marca = $Marca
        $this.Modelo = $Modelo
    }

    #Constructor 2
    Coche ([string]$Modelo)
    {
        $this.Marca = "NS"
        $this.Modelo = $Modelo
    }

    #Constructor 3
    Coche ()
    {
        $this.Marca = "No definido"
        $this.Modelo = "No definido"
    }
}

```
