# Cargar un mensaje de bienvenida en el perfil de usuario en PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2017/07/15/cargar-un-mensaje-de-bienvenida-en-el-perfil-de-usuario-en-powershell/
```PowerShell
#Para poder utilizar el fichero del perfil es necesario habilitar la ejecución de scripts
New-Item -Path $Profile.CurrentUserAllHosts -ItemType File -Force
'Write-Host "Buenos días"' | Add-Content -Path $Profile.CurrentUserAllHosts -Encoding Default

```
