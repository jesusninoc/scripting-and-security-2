# Retrieve the LastUseTime of the user profiles on system
## PowerShell 
### URL: https://www.jesusninoc.com/2017/09/06/retrieve-the-lastusetime-of-the-user-profiles-on-system/
```PowerShell
Get-WmiObject Win32_UserProfile | % {$_.LocalPath, $_.ConvertToDateTime($_.LastUseTime)}

```
