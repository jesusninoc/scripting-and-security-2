# Emitir sonidos graves con PowerShell
## Multimedia, PowerShell 
### URL: https://www.jesusninoc.com/2017/01/21/emitir-sonidos-graves-con-powershell/
```PowerShell
#Beep function
#Generates simple tones on the speaker

#Beep(Freq,Duration)
#Beep(Frecuencia,Duración)

#Freq: The frequency of the sound, in hertz
#Duration: The duration of the sound, in milliseconds

#Frecuencias en la zona "grave" del espectro (10Hz - 256Hz)
#[System.Console]::Beep(10,100) NO FUNCIONA 1OHz, EMPIEZA EN 37Hz
[System.Console]::Beep(37,100)
[System.Console]::Beep(125,100)
[System.Console]::Beep(250,100)
[System.Console]::Beep(255,100)

```
