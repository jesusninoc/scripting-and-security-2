# Comparar listas de arrays de caracteres
## PowerShell, Strings 
### URL: https://www.jesusninoc.com/2018/03/19/comparar-listas-de-arrays-de-caracteres/
```PowerShell
#Comparar con otro array y obtener los elementos que están en ambos arrays
#Array con valores
$Array=([System.Collections.Generic.HashSet[String]])::new([String[]]@("Carlos","Pedro","Lucas","Marcos","Mateo"))
$Array.IntersectWith([String[]]@("Pablo","Gonzalo","Marcos"))
$Array

#Obtener todos los elementos de los dos arrays sin repeticiones
#Array con valores
$Array=([System.Collections.Generic.HashSet[String]])::new([String[]]@("Carlos","Pedro","Lucas","Marcos","Mateo"))
$Array.UnionWith([String[]]@("Pablo","Gonzalo","Marcos"))
$Array

#Obtener los elementos de un array que no están en otro array
#Array con valores
$Array=([System.Collections.Generic.HashSet[String]])::new([String[]]@("Carlos","Pedro","Lucas","Marcos","Mateo"))
$Array.ExceptWith([String[]]@("Pablo","Gonzalo","Marcos"))
$Array

#Obtener todos los elementos de los dos arrays sin incluir los que están en los dos arrays
#Array con valores
$Array=([System.Collections.Generic.HashSet[String]])::new([String[]]@("Carlos","Pedro","Lucas","Marcos","Mateo"))
$Array.SymmetricExceptWith([String[]]@("Pablo","Gonzalo","Marcos"))
$Array

```
