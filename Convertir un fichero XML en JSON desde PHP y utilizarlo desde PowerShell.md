# Convertir un fichero XML en JSON desde PHP y utilizarlo desde PowerShell
## PHP, PowerShell 
### URL: https://www.jesusninoc.com/2018/02/26/convertir-un-fichero-xml-en-json-desde-php-y-utilizarlo-desde-powershell/
```PHP
<?php
	$xml = simplexml_load_file("fich.xml");
	$json = json_encode($xml);
	echo $json;
?>

```
```PowerShell
<?xml version="1.0"?>
<alumnos>
	<alumno id="1">
		<usuario>juanito</usuario>
		<grupo>ventas</grupo>
		<programa>notepad</programa>
		<directorio>carpetatrabajo</directorio>
		<permisos>leer</permisos>
	</alumno>
	<alumno id="2">
		<usuario>luis</usuario>
		<grupo>ventas</grupo>
		<programa>p7zip</programa>
		<directorio>carpetatrabajo</directorio>
		<permisos>444</permisos>
	</alumno>
</alumnos>

```
```PowerShell
$alumnos = (Invoke-WebRequest "http://localhost/xml.php").content | ConvertFrom-Json
$alumnos.alumno | %{$_.'@attributes',$_.usuario}

```
