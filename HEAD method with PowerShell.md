# HEAD method with PowerShell
## Network, PowerShell 
### URL: https://www.jesusninoc.com/2017/07/24/head-method-with-powershell/
```PowerShell
#The HEAD method is identical to the GET method except that the server must not return a message-body in the response.
Invoke-WebRequest -Uri 'https://jesusninoc.com' -Method Head).RawContent

```
