# Current time and date in Germany
## PowerShell 
### URL: https://www.jesusninoc.com/2016/12/05/current-time-and-date-in-germany/
```PowerShell
[TimeZoneInfo]::ConvertTime((Get-Date),[TimeZoneInfo]::FindSystemTimeZoneById("Central European Standard Time"))

```
