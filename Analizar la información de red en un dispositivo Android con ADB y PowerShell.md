# Analizar la información de red en un dispositivo Android con ADB y PowerShell
## Android, Network, PowerShell 
### URL: https://www.jesusninoc.com/2017/03/13/analizar-la-informacion-de-red-en-un-dispositivo-android-con-adb-y-powershell/
```PowerShell
$redandroid=.\adb.exe shell netstat
$redandroid

#Quitar espacios las partes de cada línea
$redandroid=$redandroid -replace("      "," ") -replace("   "," ") -replace("  "," ")

#Quitar espacios al principio y al final
$redandroid.trim() | %{$_}

#Mostrar la columna con las direcciónes IP remotas (Address)
$redandroid.trim() | %{$_.split(" ")[4]}

#Agrupar por dirección IP remota
$redandroid.trim() | %{
    $direccionremota=$_.split(" ")[4]
    if($direccionremota)
    {
        $direccionremota.split(":")[0] 
    }
} | Group-Object

#Consultar información sobre cada dirección IP agrupada
($redandroid.trim() | %{
    $direccionremota=$_.split(" ")[4]
    if($direccionremota)
    {
        $direccionremota.split(":")[0] 
    }
} | Group-Object | select Name).name | %{[Net.DNS]::GetHostEntry($_) | Format-Custom}

```
