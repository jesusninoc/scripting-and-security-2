# Convertir la primera letra de una palabra en mayúscula
## PowerShell, Strings 
### URL: https://www.jesusninoc.com/2017/02/12/convertir-la-primera-letra-de-una-palabra-en-mayuscula/
```PowerShell
$palabra="palabra"
$palabra.substring(0,1).toupper()+$palabra.substring(1).tolower()

```
