# Ver el avatar de un usuario de WordPress con PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2017/03/05/ver-el-avatar-de-un-usuario-de-wordpress-con-powershell/
```PowerShell
$json=(Invoke-WebRequest -Uri 'https://jesusninoc.com/wp-json/wp/v2/users/').content | ConvertFrom-JSON
Start-Process $json.avatar_urls.96

```
