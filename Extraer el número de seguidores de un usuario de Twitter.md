# Extraer el número de seguidores de un usuario de Twitter
## PowerShell, Web 
### URL: https://www.jesusninoc.com/2018/06/01/extraer-el-numero-de-seguidores-de-un-usuario-de-twitter/
```PowerShell
$url = "https://twitter.com/microsoft"
$result = Invoke-WebRequest $url
$result.AllElements | Where Class -eq “ProfileNav-value” | %{$_.innerText}

```
