# Mostrar los colores de primer plano de la consola en PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2018/04/06/mostrar-los-colores-de-primer-plano-de-la-consola-en-powershell/
```PowerShell
0..15 | % {Write-Host -ForegroundColor ([ConsoleColor]$_) -Object "X" -NoNewline}

```
