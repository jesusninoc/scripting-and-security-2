# Añadir elementos a una ArrayList y ordenar los elementos
## PowerShell 
### URL: https://www.jesusninoc.com/2017/08/21/anadir-elementos-a-una-arraylist-y-ordenar-los-elementos/
```PowerShell
#Inicializa una nueva instancia de la clase ArrayList que está vacía y tiene la capacidad inicial predeterminada
[System.Collections.ArrayList] $arraylist = New-Object System.Collections.ArrayList

#Agrega elementos a la clase ArrayList
[void]$arraylist.Add("uno")
[void]$arraylist.Add("dos")
[void]$arraylist.Add("tres")

#Número de elementos de ArrayList
$arraylist.Count

#ArrayList sin ordenar
$arraylist

#Ordenar elementos de ArrayList
$arraylist.Sort()

#ArrayList ordenado
$arraylist

```
