# Autenticarse en un router de fibra óptica MitraStar GPT-2541GNAC de Movistar y ver la tabla ARP
## Network, PowerShell 
### URL: https://www.jesusninoc.com/2017/05/10/autenticarse-en-un-router-de-fibra-optica-mitrastar-de-movistar-y-ver-la-tabla-arp/
```PowerShell
#Codificar el user y pass en Base64 y añadir como encabezado (Headers)
$user="1234"
$pass="12341234"
$pair="${user}:${pass}"
$bytes=[System.Text.Encoding]::ASCII.GetBytes($pair)
$base64=[System.Convert]::ToBase64String($bytes)
$basicAuthValue="$base64"
$headers=@{sessionKey=$basicAuthValue;pass=""}

#Autenticarse y almacenar la variable de sesión (SessionVariable) login
$url='http://192.168.1.1/login-login.cgi'
$result=(Invoke-WebRequest -Uri $url -Method POST -Headers $headers -SessionVariable login)

#Utilizar la variable de sesión login
$url='http://192.168.1.1/arpview.cmd'
$result=(Invoke-WebRequest -Uri $url -Method GET -WebSession $login)
($result.AllElements).outerText

```
