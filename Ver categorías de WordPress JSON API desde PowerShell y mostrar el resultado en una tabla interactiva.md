# Ver categorías de WordPress JSON API desde PowerShell y mostrar el resultado en una tabla interactiva
## PowerShell, Web 
### URL: https://www.jesusninoc.com/2018/03/30/ver-categorias-de-wordpress-json-api-desde-powershell-y-mostrar-el-resultado-en-una-tabla-interactiva/
```PowerShell
$json=(Invoke-WebRequest -Uri 'https://www.jesusninoc.com/wp-json/wp/v2/categories').content | ConvertFrom-JSON
$json.name | Out-GridView

```
