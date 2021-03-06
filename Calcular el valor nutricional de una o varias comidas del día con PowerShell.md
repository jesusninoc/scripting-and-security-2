# Calcular el valor nutricional de una o varias comidas del día con PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2018/03/20/calcular-el-valor-nutricional-de-una-o-varias-comidas-del-dia-con-powershell/
```PowerShell
# Suma de todas las Kcal de la comida 
$SumaKcal = 0

# En el fichero alimento se encuentra el nombre del producto y la cantidad consumida
# Macarrones+gallo,200
# aceituna+hojiblanca+de+cultivo,50
# Aceite+de+oliva+virgen+extra+carbonell,10
# Nueces,50
# Pan,200

foreach ($alimentos in gc .\alimentos.txt){

    # Buscar el producto sobre el que calcular el valor nutricional
    $enlaces = Invoke-WebRequest ("https://www.alcampo.es/compra-online/search/?text="+$alimentos.split(",")[0])

    # Seleccionar el primer producto de la lista y calcular con dicho producto el valor nutricional
    $web = Invoke-WebRequest ("https://www.alcampo.es/" + (($enlaces.Links | Where Class -eq "productMainLink").href)[0])

    # Sirve para ver el producto elegido
    Start-Process chrome ("https://www.alcampo.es/" + (($enlaces.Links | Where Class -eq "productMainLink").href)[0])

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

    # Calcular el valor nutricional en función de la cantidad del alimento consumida
    $comidacantidad = $alimentos.split(",")[1]

    $productos.'Peso neto escurrido'
    $productos.add('Valor energético(Kcal) Neto',($productos.'Valor energético(Kcal)' / $productos.'Peso Neto')*$comidacantidad)
    $productos.add('Hidatos de carbono Neto',($productos.'Hidratos de carbono' / $productos.'Peso Neto')*$comidacantidad)
    $productos.add('Grasas Netas',($productos.Grasas / $productos.'Peso Neto')*$comidacantidad)
    $productos.add('Grasas saturadas Netas',($productos.'Grasas saturadas' / $productos.'Peso Neto')*$comidacantidad)
    $productos.add('Azúcares Netos',($productos.Azúcares / $productos.'Peso Neto')*$comidacantidad)
    $productos.add('Proteínas Netas',($productos.Proteínas / $productos.'Peso Neto')*$comidacantidad)

    $alimentos
    [Int]$productos.'Valor energético(Kcal) Neto'
    $SumaKcal += [Int]$productos.'Valor energético(Kcal) Neto'

    # Mostrar la estructura con los valores nutricionales
    # $productos.GetEnumerator() | sort -Property name
}

# Total de Kcal consumidas
$SumaKcal

```
