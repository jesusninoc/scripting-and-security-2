# Extraer datos de una imagen mediante el reconocimiento óptico de caracteres y el análisis de imágenes (Computer Vision API de Microsoft Azure)
## PowerShell, Recognition 
### URL: https://www.jesusninoc.com/2017/12/31/extraer-datos-de-una-imagen-mediante-el-reconocimiento-optico-de-caracteres-y-el-analisis-de-imagenes-computer-vision-api-de-microsoft-azure/
```PowerShell
$vision = 'https://westcentralus.api.cognitive.microsoft.com/vision/v1.0/analyze'
$features = 'Categories,Tags,Description,Color'
$bytes = [System.IO.File]::ReadAllBytes("C:\Users\juan\Desktop\recono\coche.jpg")

$response = Invoke-WebRequest `
     -Uri "$($vision)?visualFeatures=$($features)" `
     -Body $bytes `
     -ContentType "application/octet-stream" `
     -Headers @{'Ocp-Apim-Subscription-Key' = 'Clave del API'} `
     -Method 'Post' `
     -ErrorAction Stop `
     -UseBasicParsing | ConvertFrom-Json

$response.description

```
