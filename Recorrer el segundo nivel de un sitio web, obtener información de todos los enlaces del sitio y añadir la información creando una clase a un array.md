# Recorrer el segundo nivel de un sitio web, obtener información de todos los enlaces del sitio y añadir la información creando una clase a un array
## Automation, PowerShell, Web 
### URL: https://www.jesusninoc.com/2018/01/13/recorrer-el-segundo-nivel-de-un-sitio-web-obtener-informacion-de-todos-los-enlaces-del-sitio-y-anadir-la-informacion-creando-una-clase-a-un-array/
```PowerShell
#Clase Enlace con información sobre el enlace: URL, tamaño y nivel de recorrido
class Enlace
{ 
    $URL
    $Long
    $Level

    Enlace($URL,$Long,$Level)
    {
        $this.URL=$URL
        $this.Long=$Long
        $this.Level=$Level
    }
}

#Iniciar array
$myArray = @()

#Recorrer el sitio hasta el segundo nivel, almacenando cada información (clase Enlace) en un array
$url="http://www.jesusninoc.com"
foreach($links in (Invoke-WebRequest $url).Links.href){foreach($links2 in (Invoke-WebRequest $links).Links.href)
{$myArray += [Enlace]::new($links2,(Invoke-WebRequest $links2).RawContentLength,2);start-sleep -s 4;$links2}}

$myArray

```
