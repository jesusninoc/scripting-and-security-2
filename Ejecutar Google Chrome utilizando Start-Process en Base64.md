# Ejecutar Google Chrome utilizando Start-Process en Base64
## PowerShell 
### URL: https://www.jesusninoc.com/2016/11/01/ejecutar-google-chrome-utilizando-start-process-en-base64/
```PowerShell
$command="Start-Process chrome '--chrome-frame --window-size=800,600 --window-position=580,240 --app=https://www.jesusninoc.com/'"
$code=[System.Convert]::ToBase64String([System.Text.Encoding]::Unicode.GetBytes($command))
powershell -encodedcommand $code

```
