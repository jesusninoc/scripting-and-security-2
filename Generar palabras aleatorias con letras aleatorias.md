# Generar palabras aleatorias con letras aleatorias
## PowerShell 
### URL: https://www.jesusninoc.com/2017/01/07/generar-palabras-aleatorias-con-letras-aleatorias/
```PowerShell
((65..90) + (97..122) | Get-Random -Count 5 | % {[char]$_}) -join ""

```
