# Mostrar los colores de fondo de la consola en PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2018/04/04/mostrar-los-colores-de-fondo-de-la-consola-en-powershell/
```PowerShell
0..15 | % {Write-Host -BackgroundColor ([ConsoleColor]$_) -Object " " -NoNewline}

```
