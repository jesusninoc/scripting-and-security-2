# Mira lo que sucede en este momento en Twitter con PowerShell
## Automation, PowerShell 
### URL: https://www.jesusninoc.com/2017/09/28/mira-lo-que-sucede-en-este-momento-en-twitter-con-powershell/
```PowerShell
$url="https://twitter.com/i/trends?k=&pc=true&show_context=false&src=search-home"
$result = Invoke-WebRequest $url
$json=$result.Content | ConvertFrom-Json
$json.module_html -split "`n" | Select-String "data-trend-name"

```
