# Grabar audio desde la línea de comandos descargando desde Internet SoX
## Multimedia, PowerShell 
### URL: https://www.jesusninoc.com/2017/02/07/grabar-audio-desde-la-linea-de-comandos-descargando-desde-internet-sox/
```PowerShell
#Descargar SoX
Start-BitsTransfer "https://downloads.sourceforge.net/project/sox/sox/14.4.2/sox-14.4.2-win32.zip"
#Descomprimir
Expand-Archive .\sox-14.4.2-win32.zip
#Acceder sox.exe
cd .\sox-14.4.2-win32\sox-14.4.2
#Ejecutar sox.exe
.\sox.exe -t waveaudio −d audio.wav

```
