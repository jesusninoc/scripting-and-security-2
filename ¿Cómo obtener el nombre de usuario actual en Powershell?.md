# ¿Cómo obtener el nombre de usuario actual en Powershell
## PowerShell 
### URL: https://www.jesusninoc.com/2018/06/25/como-obtener-el-nombre-de-usuario-actual-en-powershell/
```PowerShell
if ($env:USERNAME -like "*Juan*")
{
    "Usuario Juan"
}

```
