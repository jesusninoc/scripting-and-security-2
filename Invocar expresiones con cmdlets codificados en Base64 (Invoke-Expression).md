# Invocar expresiones con cmdlets codificados en Base64 (Invoke-Expression)
## PowerShell 
### URL: https://www.jesusninoc.com/2016/10/12/invocar-expresiones-con-cmdlets-codificados-en-base64-invoke-expression/
```PowerShell
#RwBlAHQALQBQAHIAbwBjAGUAcwBzAA== -> Get-Process
Invoke-Expression "powershell -encodedcommand 'RwBlAHQALQBQAHIAbwBjAGUAcwBzAA=='"

```
