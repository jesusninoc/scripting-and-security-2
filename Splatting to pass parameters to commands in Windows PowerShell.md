# Splatting to pass parameters to commands in Windows PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2016/10/29/splatting-to-pass-parameters-to-commands-in-windows-powershell/
```PowerShell
$getContentParameters = @{
'Name'='chrome'
}
Get-Process @getContentParameters

```
