# Convertir una cadena que contiene uno o más pares de claves y valores en una tabla hash
## PowerShell, Strings 
### URL: https://www.jesusninoc.com/2017/08/27/convertir-una-cadena-que-contiene-uno-o-mas-pares-de-claves-y-valores-en-una-tabla-hash/
```PowerShell
$String = @'
Marca=Audi
Modelo=A3
Color=rojo
'@ 
 
$Hash = $String | ConvertFrom-StringData
 
$Hash.Marca
$Hash.Color

```
