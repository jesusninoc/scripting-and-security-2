# Invocar expresiones con cmdlets codificados en Base64 (Invoke-Command)
## PowerShell 
### URL: https://www.jesusninoc.com/2016/10/14/invocar-expresiones-con-cmdlets-codificados-en-base64-invoke-command/
```PowerShell
$scriptblock = {powershell -encodedcommand 'RwBlAHQALQBQAHIAbwBjAGUAcwBzAA=='}
Invoke-Command -scriptblock $scriptblock

```
