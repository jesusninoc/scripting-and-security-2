# Ver los usuarios que tienen la carpeta Escritorio (Desktop)
## PowerShell 
### URL: https://www.jesusninoc.com/2017/03/28/ver-los-usuarios-que-tienen-la-carpeta-escritorio-desktop/
```PowerShell
Resolve-Path -Path C:\users\*\Desktop -ErrorAction SilentlyContinue | ForEach-Object {$_.Path.Split('\')[-2]}

```
