# Buscar Despachos de abogados con PowerShell
## PowerShell, Web scraping 
### URL: https://www.jesusninoc.com/2016/12/25/buscar-despachos-de-abogados-con-powershell/
```PowerShell
$web=Invoke-WebRequest 'https://www.empresia.es/busqueda/?q=despacho+abogados'
$web.AllElements | Where class -eq "grid" | %{$_.innertext}

```
