# Añadir elementos a una HashTable y ordenar los elementos
## PowerShell 
### URL: https://www.jesusninoc.com/2017/08/22/anadir-elementos-a-una-hashtable-y-ordenar-los-elementos/
```PowerShell
#Agrega elementos a la clase HashTable
$hashtable = @{uno='valoruno'; dos='valordos'; tres='valortres'}

#Número de elementos de HashTable
$hashtable.Count

#HashTable sin ordenar
$hashtable

#Ordenar elementos de HashTable
$hashtable.GetEnumerator() | Sort-Object -Property Value

```
