# Analizar las señales de radio y convertir a texto con Bing Speech API
## PowerShell, Radio, Recognition 
### URL: https://www.jesusninoc.com/2018/01/13/analizar-las-senales-de-radio-y-convertir-a-texto-con-bing-speech-api/
```PowerShell
#Escanear frecuencias y clasificar las señales encontradas
python predict_scan.py --start 95000000 --stop 108000000 --step 50000 --gain 20 --ppm 56 --threshold 0.9955

```
```PowerShell
#Para cada señal encontrada guardar en un fichero de audio
rtl_fm -f 106.1M -p -24 -g 40 -s 11025 - | ffmpeg.exe -f s16le -ac 1 -ar 32k -i pipe:0 -acodec libmp3lame -ab 32k -f wav fichero.wav

```
```PowerShell
#Convertir a texto el audio guardado

#Convertir voz en texto para comprender la intención del usuario (Bing Speech API)
#URI del servicio de reconocimiento
$URI = 'https://speech.platform.bing.com/speech/recognition/interactive/cognitiveservices/v1?language=ES-es&format=detailed'

#Cabeceras (incluir la clave del API)
$Cabeceras = @{
    'Ocp-Apim-Subscription-Key' = 'Clave del API';
    'Transfer-Encoding' = 'chunked'
    'Content-type' = 'audio/wav; codec=audio/pcm; samplerate=16000'
}

#Convertir el fichero WAV en Bytes
$AudioBytes = [System.IO.File]::ReadAllBytes("C:\Users\juan\Desktop\RelWithDebInfo\rtl-sdr-release\x64\fichero.wav")

#Preperar la petición y obtener respuesta
$Respuesta = Invoke-RestMethod -Method POST -Uri $URI -Headers $Cabeceras -Body $AudioBytes

#Convertir respuesta en formato JSON
ConvertTo-Json $Respuesta

```
