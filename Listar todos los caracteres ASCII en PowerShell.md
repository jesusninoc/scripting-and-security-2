# Listar todos los caracteres ASCII en PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2017/10/08/listar-todos-los-caracteres-ascii-en-powershell/
```PowerShell
0..255 | %{[Char]$_}

```
