# Ejecutar la información que se encuentra en un valor dentro de la clave CLSID del Registro de Windows
## PowerShell, Registry 
### URL: https://www.jesusninoc.com/2018/06/04/ejecutar-la-informacion-que-se-encuentra-en-un-valor-dentro-de-la-clave-clsid-del-registro-de-windows/
```PowerShell
# Generar un GUID
$guid = $([guid]::NewGuid().Guid);$guid

# Añadir nueva entrada al registro
reg add HKCU\Software\Classes\CLSID\$("{"+$guid+"}")\Shell\Manage\command /ve /t REG_SZ /d "calc.exe"

# Ejecutar la entrada del registro
rundll32 url.dll, OpenURL shell:::$("{"+$guid+"}")

```
