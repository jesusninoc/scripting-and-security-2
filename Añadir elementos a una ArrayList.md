# Añadir elementos a una ArrayList
## PowerShell 
### URL: https://www.jesusninoc.com/2017/09/11/anadir-elementos-a-una-arraylist/
```PowerShell
#Inicializa una nueva instancia de la colección ArrayList que está vacía y tiene la capacidad inicial predeterminada
[System.Collections.ArrayList] $arraylist = New-Object System.Collections.ArrayList

#Agrega elementos a la colección ArrayList
[void]$arraylist.Add("uno")
[void]$arraylist.Add("dos")
[void]$arraylist.Add("tres")

#Número de elementos de ArrayList
$arraylist.Count

```
