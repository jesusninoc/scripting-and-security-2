# Leer el texto contenido dentro de un fichero mediante la voz del Sistema Operativo
## Automation, PowerShell 
### URL: https://www.jesusninoc.com/2016/12/31/leer-el-texto-contenido-dentro-de-un-fichero-mediante-la-voz-del-sistema-operativo/
```PowerShell
Add-Type -AssemblyName System.Speech
 
gc E:\aleer\fichero.txt | %{
$synthesizer = New-Object -TypeName System.Speech.Synthesis.SpeechSynthesizer
$_
#Establece la velocidad de habla de la SpeechSynthesizer
$synthesizer.Rate=0
$synthesizer.Speak($_)
}

```
