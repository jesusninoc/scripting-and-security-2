# WordPress username enumeration with PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2017/03/04/wordpress-username-enumeration-with-powershell/
```PowerShell
$json=(Invoke-WebRequest -Uri 'https://jesusninoc.com/wp-json/wp/v2/users/').content | ConvertFrom-JSON
$json.name

```
