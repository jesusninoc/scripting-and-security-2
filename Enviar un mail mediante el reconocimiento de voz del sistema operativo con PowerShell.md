# Enviar un mail mediante el reconocimiento de voz del sistema operativo con PowerShell
## Multimedia, PowerShell, Recognition 
### URL: https://www.jesusninoc.com/2017/01/09/enviar-un-mail-mediante-el-reconocimiento-de-voz-del-sistema-operativo-con-powershell/
```PowerShell
[void][reflection.assembly]::loadwithpartialname(‘system.speech’)
$rec = New-Object ‘System.Speech.Recognition.SpeechRecognitionEngine’
$rec.LoadGrammar((New-Object ‘System.Speech.Recognition.DictationGrammar’))
$rec.SetInputToDefaultAudioDevice()
 
do
{
if($rec.Recognize().Text -match "mail")
{
"Enviar correo"
Send-MailMessage -to "mail2@example.com" -from “mail@example.com” -subject "Correo prueba" -SmtpServer localhost
}
}while(1)

```
