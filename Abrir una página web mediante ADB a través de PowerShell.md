# Abrir una página web mediante ADB a través de PowerShell
## Android 
### URL: https://www.jesusninoc.com/2017/03/25/abrir-una-pagina-web-mediante-adb-a-traves-de-powershell/
```PowerShell
.\adb.exe shell am start -a android.intent.action.VIEW -c android.intent.category.BROWSABLE -d https://jesusninoc.com

```
