﻿# Abrir Chrome en modo incógnito desde PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2018/03/09/abrir-chrome-en-modo-incognito-desde-powershell/
```PowerShell
[System.Diagnostics.Process]::Start("chrome.exe", "--incognito $url")
```
