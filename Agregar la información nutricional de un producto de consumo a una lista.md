# Agregar la información nutricional de un producto de consumo a una lista
## PowerShell 
### URL: https://www.jesusninoc.com/2018/03/12/agregar-la-informacion-nutricional-de-un-producto-de-consumo-a-una-lista/
```PowerShell
$web = Invoke-WebRequest "https://www.alcampo.es/compra-online/productos-frescos/pescados-y-mariscos/anchoas-y-boquerones/anchoas/consorcio-anchoa-en-aceite-de-oliva-29-gramos/p/60139"

$productos = @{}

($web.AllElements | Where Class -eq “productNutritionalInformation valoresNutricionalesTabla”).innerHtml | %{
    ($_ -replace "</SPAN> <SPAN ","</SPAN>|<SPAN " -replace "<.*?>" -replace " g" -replace " Kj" -replace " Kcal" -split "`n" | ? {$_.trim() -ne ""} | ? {$_.trim() -notmatch "nutricionales"}).trim()
} | %{$productos.add($_.split("|")[0],$_.split("|")[1])}

$productos

```
