# Obtener datos de una base de datos y almacenar el contenido en un fichero de texto
## PowerShell 
### URL: https://www.jesusninoc.com/2017/08/07/obtener-datos-de-una-base-de-datos-y-almacenar-el-contenido-en-un-fichero-de-texto/
```PowerShell
#Leer datos de una base de datos y almacenar en un fichero con el nombre del ID de cada registro
[void][System.Reflection.Assembly]::LoadWithPartialName("MySql.Data")
$Connection = New-Object MySql.Data.MySqlClient.MySqlConnection
$ConnectionString = "server=" + "localhost" + ";port=3306;uid=" + "root" + ";pwd=" + ";database="+"gps"
$Connection.ConnectionString = $ConnectionString
$Connection.Open()

$Query='select * from result'
$Command = New-Object MySql.Data.MySqlClient.MySqlCommand($Query, $Connection)
$DataAdapter = New-Object MySql.Data.MySqlClient.MySqlDataAdapter($Command)
$DataSet = New-Object System.Data.DataSet
$RecordCount = $dataAdapter.Fill($dataSet, "data")
$Connection.Close()

#Almacenar el contenido de cada registro obtenido de la consulta a la base de datos en un fichero
foreach($valor in $DataSet.Tables[0])
{
$valor.ID
$valor | Out-File $valor.id 
}

```
