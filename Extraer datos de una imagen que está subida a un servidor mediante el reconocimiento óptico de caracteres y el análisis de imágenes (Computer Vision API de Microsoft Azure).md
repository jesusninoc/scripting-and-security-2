# Extraer datos de una imagen que está subida a un servidor mediante el reconocimiento óptico de caracteres y el análisis de imágenes (Computer Vision API de Microsoft Azure)
## PowerShell, Recognition 
### URL: https://www.jesusninoc.com/2018/01/06/extraer-datos-de-imagenes-que-estan-subidas-a-un-servidor-mediante-el-reconocimiento-optico-de-caracteres-y-el-analisis-de-imagenes-computer-vision-api-de-microsoft-azure/
```PowerShell
#URI del servicio de reconocimiento
$URI = 'https://westcentralus.api.cognitive.microsoft.com/vision/v1.0/analyze'

#Características que serán analizadas
$features = 'Categories,Tags,Description,Color'

#Cabeceras (incluir la clave del API)
$Cabeceras = @{
  'Ocp-Apim-Subscription-Key' = 'Clave del API';
  'Content-type' = 'application/json'
}

#URL de la imagen
$Body = '{"url":"http://www.abc.es/media/motor/2017/09/26/accidente-puigdemont-kZiE--510x286@abc.JPG"}'

#Preperar la petición y obtener respuesta
$Respuesta = Invoke-RestMethod -Method Post -Uri ($URI+"?visualFeatures=$($features)") -Headers $Cabeceras -Body $Body

#Convertir respuesta en formato JSON
ConvertTo-Json $Respuesta

```
