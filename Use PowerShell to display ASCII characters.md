# Use PowerShell to display ASCII characters
## PowerShell 
### URL: https://www.jesusninoc.com/2016/12/09/use-powershell-to-display-ascii-characters/
```PowerShell
0..255 | %{Write-Host ([char]$_ +" ") -NoNewline}

```
