# Comparar listas de arrays de números
## PowerShell 
### URL: https://www.jesusninoc.com/2018/02/03/comparar-listas-de-arrays/
```PowerShell
#Comparar con otro array y obtener los elementos que están en ambos arrays
#Array con valores
$Array=([System.Collections.Generic.HashSet[int32]])::new([int[]]@(1,2,3,4,5,6))
$Array.IntersectWith([int[]]@(5,6,7,8,9,10))
$Array

#Obtener todos los elementos de los dos arrays sin repeticiones
#Array con valores
$Array=([System.Collections.Generic.HashSet[int32]])::new([int[]]@(1,2,3,4,5,6))
$Array.UnionWith([int[]]@(5,6,7,8,9,10))
$Array

#Obtener los elementos de un array que no están en otro array
#Array con valores
$Array=([System.Collections.Generic.HashSet[int32]])::new([int[]]@(1,2,3,4,5,6))
$Array.ExceptWith([int[]]@(5,6,7,8,9,10))
$Array

#Obtener todos los elementos de los dos arrays sin incluir los que están en los dos arrays
#Array con valores
$Array=([System.Collections.Generic.HashSet[int32]])::new([int[]]@(1,2,3,4,5,6))
$Array.SymmetricExceptWith([int[]]@(5,6,7,8,9,10))
$Array

```
