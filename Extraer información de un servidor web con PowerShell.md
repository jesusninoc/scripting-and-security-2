# Extraer información de un servidor web con PowerShell
## PowerShell, Web 
### URL: https://www.jesusninoc.com/2016/11/13/extraer-informacion-de-un-servidor-web-con-powershell/
```PowerShell
#Leer un fichero TXT que se ha subido a un servidor
$fichero='https://www.jesusninoc.com/wp-content/uploads/2016/11/fichero.txt'
$result = Invoke-WebRequest $fichero
$result.Content

#Descargar un fichero TXT que se ha subido a un servidor
$fichero='https://www.jesusninoc.com/wp-content/uploads/2016/11/fichero.txt'
$result = Start-BitsTransfer $fichero
gc .\fichero.txt

#Extraer información de una web
$url='https://www.jesusninoc.com/2011/01/01/jesusninoc/'
$result = Invoke-WebRequest $url
$result.AllElements | Where Class -eq “crayon-line” | %{$_.innerText}

```
