# Cambiar el estado de carga de batería en Android con ADB
## Android 
### URL: https://www.jesusninoc.com/2017/03/06/cambiar-el-estado-de-carga-de-bateria-en-android-con-adb/
```PowerShell
#0	Status
#1	Unknown
#2	Charging
#3	Discharging
#4	Not charging
#5	Full

.\adb.exe shell dumpsys battery set status 3
.\adb.exe shell dumpsys battery set status 2

#Reiniciar la carga normal
.\adb shell dumpsys battery reset

```
