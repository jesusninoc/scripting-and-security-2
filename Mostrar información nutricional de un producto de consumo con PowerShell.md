# Mostrar información nutricional de un producto de consumo con PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2018/02/18/mostrar-informacion-nutricional-de-un-producto-de-consumo-con-powershell/
```PowerShell
$web = Invoke-WebRequest "https://www.alcampo.es/compra-online/productos-frescos/pescados-y-mariscos/anchoas-y-boquerones/anchoas/consorcio-anchoa-en-aceite-de-oliva-29-gramos/p/60139"
$web.AllElements | Where Class -eq “productNutritionalInformation valoresNutricionalesTabla” | %{$_.innerText}

```
