# Descargar las imágenes de una página web
## PowerShell, Web, Web scraping 
### URL: https://www.jesusninoc.com/2018/05/20/descargar-las-imagenes-de-una-pagina-web/
```PowerShell
$url = "https://www.jesusninoc.com/2018/05/13/get-rss-feed-from-jesusninoc-com-new-version/"
$result = Invoke-WebRequest $url
$result.Images.src | %{Start-BitsTransfer -Source $_}

```
