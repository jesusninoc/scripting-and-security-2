# Convertir ficheros de audio a texto
## Automation, Multimedia, PowerShell, Recognition 
### URL: https://www.jesusninoc.com/2016/12/25/convertir-ficheros-de-audio-a-texto/
```PowerShell
#Abrir un fichero WAV y convertir a texto el contenido

#Más información: https://msdn.microsoft.com/en-us/library/ms720151(v=vs.85).aspx#API_Speech_Recognition

[void][reflection.assembly]::loadwithpartialname('system.speech')
$rec = New-Object 'System.Speech.Recognition.SpeechRecognitionEngine'
$rec.RecognizerInfo.Description
$rec.LoadGrammar((New-Object 'System.Speech.Recognition.DictationGrammar'))
ls e:\ *.mp3 | %{
$rec.SetInputToWaveFile($_.FullName)
$rec.Recognize().Text
}

```
