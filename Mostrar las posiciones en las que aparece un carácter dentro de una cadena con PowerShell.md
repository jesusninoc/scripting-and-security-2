# Mostrar las posiciones en las que aparece un carácter dentro de una cadena con PowerShell
## PowerShell, Strings 
### URL: https://www.jesusninoc.com/2018/06/26/mostrar-las-posiciones-en-las-que-aparece-un-caracter-dentro-de-una-cadena-con-powershell/
```PowerShell
# Mostras las posiciones en las que aparece el carácter "r" dentro de una cadena
((Help) | Select-String "r" -AllMatches).Matches.Index

```
