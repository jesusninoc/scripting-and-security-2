# Mostrar los restaurantes más reservados de Madrid
## PowerShell, Web, Web scraping 
### URL: https://www.jesusninoc.com/2018/06/06/mostrar-los-restaurantes-mas-reservados-de-madrid/
```PowerShell
$url = "https://www.eltenedor.es/ciudad/madrid/328022"
$result = Invoke-WebRequest $url
#La etiqueta que tenemos buscar es: class="restaurantSelection-name
$result.AllElements | Where Class -eq “restaurantSelection-name” | %{$_.innerText}

```
