# Ver las voces disponibles en el sistema operativo
## Multimedia, PowerShell 
### URL: https://www.jesusninoc.com/2017/03/13/ver-las-voces-disponibles-en-el-sistema-operativo/
```PowerShell
Add-Type -AssemblyName System.Speech
$voz = New-Object System.Speech.Synthesis.SpeechSynthesizer
$voz.GetInstalledVoices() | Select-Object -ExpandProperty VoiceInfo | Select-Object -Property Culture, Name

```
