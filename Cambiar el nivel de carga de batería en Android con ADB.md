# Cambiar el nivel de carga de batería en Android con ADB
## Android 
### URL: https://www.jesusninoc.com/2017/03/05/cambiar-el-nivel-de-carga-de-bateria-en-android-con-adb/
```PowerShell
#Poner nivel de carga de batería a 3
.\adb.exe shell dumpsys battery set level 3

#Reiniciar la carga normal
.\adb shell dumpsys battery reset

```
