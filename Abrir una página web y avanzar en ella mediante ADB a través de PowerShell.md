# Abrir una página web y avanzar en ella mediante ADB a través de PowerShell
## Android, PowerShell, Web 
### URL: https://www.jesusninoc.com/2016/10/24/abrir-una-pagina-web-y-avanzar-en-ella-mediante-adb-a-traves-de-powershell/
```PowerShell
#Abrir Google Chrome en Android mediante ADB
#Es necesario habilitar el modo depuración en Android
cd "D:\program\android-sdk-windows\platform-tools"
.\adb shell am start -n com.android.chrome/com.google.android.apps.chrome.Main -d 'https://twitter.com/microsoft'
Start-Sleep -Seconds 5
#Ir avanzando en la página web mediante avanzar página
$avanzar=0
do
{
.\adb shell input keyevent KEYCODE_PAGE_DOWN
Start-Sleep -Seconds 5
$avanzar+=1
}while($avanzar -lt 10)

```
