# Acceder a los datos publicados en un formulario de Google desde PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2017/05/01/acceder-a-los-datos-publicados-en-un-formulario-de-google-desde-powershell/
```PowerShell
Invoke-WebRequest "https://docs.google.com/spreadsheets/d/1E11fdrON_O2fMCXcFLVkHmKi3-59Mv4qDC9Cczghkn4/pub?output=csv" -OutFile result.csv
Import-Csv .\result.csv

```
