# Emitir sonidos agudos con PowerShell
## Multimedia, PowerShell 
### URL: https://www.jesusninoc.com/2017/01/18/emitir-sonidos-agudos-con-powershell/
```PowerShell
#Beep function
#Generates simple tones on the speaker

#Beep(Freq,Duration)
#Beep(Frecuencia,Duración)

#Freq: The frequency of the sound, in hertz
#Duration: The duration of the sound, in milliseconds

#Frecuencias en la zona "aguda" del espectro (2000Hz - 16000hz).
[System.Console]::Beep(2000,100)
[System.Console]::Beep(2000,100)
[System.Console]::Beep(4000,100)
[System.Console]::Beep(16000,100)

```
