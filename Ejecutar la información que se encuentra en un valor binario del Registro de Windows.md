# Ejecutar la información que se encuentra en un valor binario del Registro de Windows
## PowerShell, Registry 
### URL: https://www.jesusninoc.com/2018/05/07/ejecutar-la-informacion-que-se-encuentra-en-un-valor-binario-del-registro-de-windows/
```PowerShell
# Almacenar información convertida a byte en un valor binario del Registro de Windows
# La información que vamos a almacenar en el registro es arrancar la calculadora de Windows
[System.Text.Encoding] $enc = [System.Text.Encoding]::UTF8
[byte[]] $rawdata = $enc.GetBytes('start calc')
$rawdata
New-ItemProperty -Path 'HKCU:\Volatile Environment' -Name Test2 -PropertyType Binary -Value $rawdata

# Ejecutar la información almacenada en el Registro
[System.Text.Encoding] $enc = [System.Text.Encoding]::UTF8
$enc.GetString((Get-ItemProperty 'HKCU:\Volatile Environment' -Name Test2).Test2) | iex

```
