# Crear objetos en PowerShell 5
## PowerShell 
### URL: https://www.jesusninoc.com/2017/02/08/crear-objetos-en-powershell-5/
```PowerShell
#Clase coche con propiedades
class Coche
{ 
  $Marca
  $Modelo
  $Color
}
 
#Crear objeto coche de la clase Coche
$coche=New-Object -TypeName Coche

#Otra forma de crear objeto coche de la clase Coche
$coche=[Coche]::new()

```
