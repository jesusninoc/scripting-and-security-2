# Mostrar los procesos que se están ejecutando en Windows con WMIC
## Processes 
### URL: https://www.jesusninoc.com/2018/05/01/mostrar-los-procesos-que-se-estan-ejecutando-en-windows-con-wmic/
```PowerShell
# Listar procesos
wmic process

# Listar procesos en formato tabla
wmic process list full /format:table

# Listar procesos en formato lista
wmic process list full /format:list

# Almacenar procesos en formato CSV
wmic /output:test.csv process list full /format:csv
Get-Content .\test.csv

# Almacenar procesos en formato HTML
wmic /output:test.html process list brief /format:htable
start chrome .\test.html

# Almacenar procesos en formato XML
wmic /output:test.xml process list full /format:xml
Get-Content .\test.xml

```
