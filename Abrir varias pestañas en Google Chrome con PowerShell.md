# Abrir varias pestañas en Google Chrome con PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2016/11/24/abrir-varias-pestanas-en-google-chrome-con-powershell/
```PowerShell
$url1="https://www.jesusninoc.com"

1..8 | %{
Start-Process chrome.exe -ArgumentList @('-incognito',$url1)
}

```
