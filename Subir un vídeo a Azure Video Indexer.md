# Subir un vídeo a Azure Video Indexer
## PowerShell, Recognition 
### URL: https://www.jesusninoc.com/2018/01/18/subir-un-video-a-azure-video-indexer/
```PowerShell
#URI del servicio Azure Video Indexer
$vision = 'https://videobreakdown.azure-api.net/Breakdowns/Api/Partner/Breakdowns'
#URL del vídeo que se va a subir
$videoUrl = "https://www.jesusninoc.com/wp-content/uploads/2017/12/Introducción-a-Bash.mp4"

#Petición POST con los parametros necesarios para subir el vídeo
$response = Invoke-WebRequest `
     -Uri ($vision + "?name=some_name&description=some_description&privacy=private&partition=some_partition&videoUrl=" + $videoUrl) `
     -ContentType "application/octet-stream" `
     -Headers @{'Ocp-Apim-Subscription-Key' = 'Clave del API'} `
     -Method 'Post' `
     -ErrorAction Stop `
     -UseBasicParsing | ConvertFrom-Json

#Obtener el id del vídeo
$response

#Comprobar si se ha subido el vídeo mediante con el id del vídeo (método GET)
$response2 = Invoke-WebRequest `
     -Uri ($vision + "/" + $response + "/State") `
     -Headers @{'Ocp-Apim-Subscription-Key' = 'Clave del API'} `
     -Method 'Get' `
     -ErrorAction Stop `
     -UseBasicParsing | ConvertFrom-Json

$response2

```
