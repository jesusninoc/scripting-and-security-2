# Dividir en grupos una cadena
## PowerShell, Strings 
### URL: https://www.jesusninoc.com/2017/02/21/dividir-en-grupos-una-cadena/
```PowerShell
'1234512345123451234512345123451234512345' -split '(?<=\G\d{5})(?=.)'

```
