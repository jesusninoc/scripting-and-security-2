# Conectar a MySQL desde PowerShell
## Database, PowerShell 
### URL: https://www.jesusninoc.com/2017/12/13/conectar-a-mysql-desde-powershell/
```PowerShell
#Conectar con MySQL

#Cargar el espacio de nombres MySql.Data que proporciona acceso a clases que representan la arquitectura ADO.NET
[void][System.Reflection.Assembly]::LoadWithPartialName("MySql.Data")

#Crear un objeto MySql.Data.MySqlClient.MySqlConnection que representa una conexión abierta a una base de datos del servidor MySQL
#Indicar en el constructor los paramétros necesarios para realizar la conexión: server, port, uid, pwd y database
$Connection = ([MySql.Data.MySqlClient.MySqlConnection]::new("server=" + "localhost" + ";port=3306;uid=" + "root" + ";pwd=" + ";database="+"estado"))
#Ejecutar el método Open para conectar a la base de datos de MySQL
$Connection.Open()

#Hacer una consulta a la base de datos

#Crear un objeto MySql.Data.MySqlClient.MySqlCommand que representa una instrucción SQL para ejecutar contra una base de datos MySQL
#Indicar en el constructor la instrucción SQL para ejecutar y la conexión (realizada en el paso anterior)
$Query = 'Select Estado from Persons'
$Command = [MySql.Data.MySqlClient.MySqlCommand]::new($Query, $Connection)

#Crear un objeto MySql.Data.MySqlClient.MySqlDataAdapter que representa un conjunto de comandos de datos y una conexión de base de datos que se utilizan para llenar un conjunto de datos y actualizar una base de datos MySQL
#Indicar en el constructor el objeto MySql.Data.MySqlClient.MySqlCommand creado anteriormente
$DataAdapter = [MySql.Data.MySqlClient.MySqlDataAdapter]::new($Command)

#Crear un objeto System.Data.DataSet que representa una caché de datos en memoria en donde se almacenan los datos obtenidos del objeto MySql.Data.MySqlClient.MySqlDataAdapter
$DataSet = [System.Data.DataSet]::new()
#Agregar en System.Data.DataSet los datos del objeto MySql.Data.MySqlClient.MySqlDataAdapter
$DataAdapter.Fill($DataSet)
#Mostrar los datos que contiene System.Data.DataSet
$DataSet.Tables

#Cerrar la conexión con MySQL cerrando el objeto MySql.Data.MySqlClient.MySqlConnection
$Connection.Close()

```
