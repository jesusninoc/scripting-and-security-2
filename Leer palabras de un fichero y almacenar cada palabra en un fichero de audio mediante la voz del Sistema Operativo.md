# Leer palabras de un fichero y almacenar cada palabra en un fichero de audio mediante la voz del Sistema Operativo
## Automation, Multimedia, PowerShell 
### URL: https://www.jesusninoc.com/2016/12/24/leer-palabras-de-un-fichero-y-almacenar-cada-palabra-en-un-fichero-de-audio-mediante-la-voz-del-sistema-operativo/
```PowerShell
Add-Type -AssemblyName System.Speech

gc .\palabras.txt | %{
$synthesizer = New-Object -TypeName System.Speech.Synthesis.SpeechSynthesizer
$path = "E:\"+$_+".mp3"
$synthesizer.SetOutputToWaveFile($path)
$synthesizer.Speak($_)
$synthesizer.SetOutputToDefaultAudioDevice()
}

```
