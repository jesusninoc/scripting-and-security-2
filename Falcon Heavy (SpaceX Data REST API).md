# Falcon Heavy (SpaceX Data REST API)
## PowerShell 
### URL: https://www.jesusninoc.com/2018/02/07/falcon-heavy-spacex-data-rest-api/
```PowerShell
Invoke-WebRequest "https://api.spacexdata.com/v2/launches/latest" | ConvertFrom-Json
Start-Process chrome (Invoke-WebRequest "https://api.spacexdata.com/v2/launches/latest" | ConvertFrom-Json).links.mission_patch

```
