# Listar las empresas del IBEX 35 que suben
## PowerShell, Web, Web scraping 
### URL: https://www.jesusninoc.com/2017/01/29/listar-las-empresas-del-ibex-35-que-suben/
```PowerShell
$web=Invoke-WebRequest 'http://www.bolsamadrid.es/esp/aspx/Mercados/Precios.aspx?indice=ESI100000000'
$web.AllElements | Where Class -eq “DifFlSb” | %{$_.innerText}

```
