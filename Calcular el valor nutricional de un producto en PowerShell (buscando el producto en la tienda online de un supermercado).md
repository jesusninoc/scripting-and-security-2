# Calcular el valor nutricional de un producto en PowerShell (buscando el producto en la tienda online de un supermercado)
## PowerShell 
### URL: https://www.jesusninoc.com/2018/03/22/calcular-el-valor-nutricional-de-un-producto-en-powershell-buscando-el-producto-en-la-tienda-online-del-supermercado/
```PowerShell
# Buscar el producto sobre el que calcular el valor nutricional
$enlaces = Invoke-WebRequest "https://www.alcampo.es/compra-online/search/?text=macarrones+gallo"

# Seleccionar el primer producto de la lista y calcular con dicho producto el valor nutricional
$web = Invoke-WebRequest ("https://www.alcampo.es/" + (($enlaces.Links | Where Class -eq "productMainLink").href)[0])

# Datos nutricionales del producto
$productos = @{}

# Extraer los valores nutricionales del producto
($web.AllElements | Where Class -eq “productNutritionalInformation valoresNutricionalesTabla”).innerHtml | %{
    ($_ -replace "</SPAN> <SPAN ","</SPAN>|<SPAN " -replace "<.*?>" -replace " g" -replace " Kj" -replace " Kcal" -split "`n" | ? {$_.trim() -ne ""} | ? {$_.trim() -notmatch "nutricionales"}).trim()
} | %{$productos.add($_.split("|")[0],$_.split("|")[1])}

$pesos = ($web.AllElements | Where Class -eq “productNutritionalInformation valoresNutricionalesTabla tablaInformacionAdicional”).innerText | %{
    ($_  -replace "<.*?>" -split "`n" | ? {$_.trim() -ne ""}).trim() -replace "g"
}

# Añadir los valores nutricionales del producto a la estructura
0..$pesos.Count | % {if($_%2-eq 0 -and $_ -lt 19){$productos.add($pesos[$_],$pesos[$_+1])}}

# Calcular el valor nutricional en función de la cantidad del alimento consumido
$comidacantidad = 100

$productos.'Peso neto escurrido'
$productos.add('Valor energético(Kcal) Neto',($productos.'Valor energético(Kcal)' / $productos.'Peso Neto')*$comidacantidad)
$productos.add('Hidatos de carbono Neto',($productos.'Hidratos de carbono' / $productos.'Peso Neto')*$comidacantidad)
$productos.add('Grasas Netas',($productos.Grasas / $productos.'Peso Neto')*$comidacantidad)
$productos.add('Grasas saturadas Netas',($productos.'Grasas saturadas' / $productos.'Peso Neto')*$comidacantidad)
$productos.add('Azúcares Netos',($productos.Azúcares / $productos.'Peso Neto')*$comidacantidad)
$productos.add('Proteínas Netas',($productos.Proteínas / $productos.'Peso Neto')*$comidacantidad)

# Mostrar la estructura con los valores nutricionales
$productos.GetEnumerator() | sort -Property name

```
