# Autenticarse en un router de fibra óptica Comtrend VG-8050 de Movistar mediante el usuario y la contraseña con PowerShell
## Network, PowerShell 
### URL: https://www.jesusninoc.com/2017/03/02/autenticarse-en-un-router-de-fibra-optica-comtrend-vg-8050-de-movistar-mediante-el-usuario-y-la-contrasena-con-powershell/
```PowerShell
$user="1234"
$pass="1234"
$pair="${user}:${pass}"
$bytes=[System.Text.Encoding]::ASCII.GetBytes($pair)
$base64=[System.Convert]::ToBase64String($bytes)
$basicAuthValue="Basic $base64"
$headers=@{Authorization=$basicAuthValue}

$url='http://192.168.1.1/info.html'
$result=(Invoke-WebRequest -Uri $url -Headers $headers)
($result.AllElements | Where class -eq “hd”).outerText

```
