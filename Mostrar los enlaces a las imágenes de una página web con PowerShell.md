# Mostrar los enlaces a las imágenes de una página web con PowerShell
## PowerShell, Web, Web scraping 
### URL: https://www.jesusninoc.com/2018/05/19/mostrar-los-enlaces-a-las-imagenes-de-una-pagina-web/
```PowerShell
$url = "https://www.jesusninoc.com/2018/05/13/get-rss-feed-from-jesusninoc-com-new-version/"
$result = Invoke-WebRequest $url
$result.Images.src

```
