# Convertir el fichero XML con la lista de radares de España en un fichero JSON utilizando PHP desde PowerShell
## PHP, PowerShell 
### URL: https://www.jesusninoc.com/2018/03/07/convertir-el-fichero-xml-con-la-lista-de-radares-de-espana-utilizando-php-desde-powershell/
```PowerShell
cd C:\xampp\php

$radares = '<?php $xml = simplexml_load_file("http://www.dgt.es/images/Tramos_INVIVE_12042017.xml"); $json = json_encode($xml); echo $json; ?>'  | .\php.exe | ConvertFrom-Json
$radares.PROVINCIA.CARRETERA | %{$_.DENOMINACION + "|" + $_.RADAR.PUNTO_INICIAL.PK}

```
