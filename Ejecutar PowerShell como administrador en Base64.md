# Ejecutar PowerShell como administrador en Base64
## PowerShell 
### URL: https://www.jesusninoc.com/2016/11/23/ejecutar-powershell-como-administrador-en-base64/
```PowerShell
$command="Start-Process PowerShell –Verb RunAs"
$code=[System.Convert]::ToBase64String([System.Text.Encoding]::Unicode.GetBytes($command))
powershell -encodedcommand $code

```
