# Crear un fichero HTML con el contenido de la tabla posts de WordPress con PowerShell
## Automation, PowerShell 
### URL: https://www.jesusninoc.com/2017/09/20/crear-un-fichero-html-con-el-contenido-de-la-tabla-posts-de-wordpress-con-powershell/
```PowerShell
#Conexión a MySQL
[void][System.Reflection.Assembly]::LoadWithPartialName("MySql.Data")
$Connection = New-Object MySql.Data.MySqlClient.MySqlConnection
$ConnectionString = "server=" + "localhost" + ";port=3306;uid=" + "root" + ";pwd=" + ";database="+"jesusninoc"
$Connection.ConnectionString = $ConnectionString
$Connection.Open()

#Consulta para obtener título y contenido a la base de datos de Wordpress
$Query='select post_title, post_content from wp_posts where id=5'
$Command = New-Object MySql.Data.MySqlClient.MySqlCommand($Query, $Connection)
$DataAdapter = New-Object MySql.Data.MySqlClient.MySqlDataAdapter($Command)
$DataSet = New-Object System.Data.DataSet
$RecordCount = $dataAdapter.Fill($dataSet, "data")
$DataSet.Tables[0].post_content

#Para cada elemento de la tabla añadir al documento HMTL
$DataSet.Tables[0] | %{
"<title>"+$_.post_title+"</title>" | Out-File output.html
"<H1>"+$_.post_title+"</H1>" | Out-File output.html -Append
$_.post_content | Out-File output.html -Append
}

#Cerrar conexión a MySQL
$Connection.Close()

#Abrir el PDF creado
Start-Process .\output.html

```
