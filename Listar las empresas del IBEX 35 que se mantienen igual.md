# Listar las empresas del IBEX 35 que se mantienen igual
## PowerShell, Web, Web scraping 
### URL: https://www.jesusninoc.com/2017/02/01/listar-las-empresas-del-ibex-35-que-se-mantienen-igual/
```PowerShell
$web=Invoke-WebRequest 'http://www.bolsamadrid.es/esp/aspx/Mercados/Precios.aspx?indice=ESI100000000'
$web.AllElements | Where Class -eq “DifFlIg” | %{$_.innerText}

```
