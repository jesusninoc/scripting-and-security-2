# Pronunciar textos con distintas voces del sistema operativo
## Multimedia, PowerShell 
### URL: https://www.jesusninoc.com/2017/11/22/pronunciar-textos-con-distintas-voces-del-sistema-operativo/
```PowerShell
$text = "
<LANG LANGID=""409"">I play</LANG>
<LANG LANGID=""407""><PITCH MIDDLE = '2'>Ich spiele</PITCH></LANG>
<LANG LANGID=""407"">Ich spiele</LANG>
<LANG LANGID=""407"">Yo juego</LANG>
" 
 
$speaker = New-Object -ComObject Sapi.SpVoice 
$speaker.Rate = 0
$speaker.Speak($text)

```
