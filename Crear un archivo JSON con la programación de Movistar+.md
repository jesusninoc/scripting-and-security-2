# Crear un archivo JSON con la programación de Movistar+
## Bash, PHP 
### URL: https://www.jesusninoc.com/2018/06/26/crear-un-archivo-json-con-la-programacion-de-movistar/
```PHP
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<?php 
	$url = "http://akamaicache.dof6.com/vod/yomvi.svc/samsung_tizen/profiles/OTT/channels?parentalRating=M18&showNonRated=true";
	$json = file_get_contents($url);
	$nombre_archivo = "movistar.php";
	
	if($archivo = fopen($nombre_archivo, "w"))
	{
		if(fwrite($archivo,  $json))
		{
			echo "Se ha ejecutado correctamente";
		}
		else
		{
			echo "Ha habido un problema al crear el archivo";
		}
		fclose($archivo);
	}
?>

```
```Shell
wget --spider https://www.jesusninoc.com/s/movis.php > /dev/null 2>&1

```
```Shell
*/15 * * * * usuario sh /tmp/movis.sh

```
```Shell
sudo /etc/init.d/cron status
sudo /etc/init.d/cron start

```
