# Detectar las palabras que están mal escritas en varias noticias de un diario con un comando en Linux y ejecutarlo con WSL (Windows Subsystem for Linux) desde PowerShell
## Bash, PowerShell 
### URL: https://www.jesusninoc.com/2018/06/29/detectar-las-palabras-que-estan-mal-escritas-en-varias-noticias-de-un-diario-con-un-comando-en-linux-y-ejecutarlo-con-wsl-windows-subsystem-for-linux-desde-powershell/
```PowerShell
# Descargar el fichero RSS con las noticias
$web = (Invoke-WebRequest "https://rss.elconfidencial.com/espana/").content

# Convertir para ver las palabras con acentos
$utf8 = [System.Text.Encoding]::GetEncoding(65001)
$iso88591 = [System.Text.Encoding]::GetEncoding(28591) #ISO 8859-1 ,Latin-1
$wrong_bytes = $utf8.GetBytes($web)
$right_bytes = [System.Text.Encoding]::Convert($utf8,$iso88591,$wrong_bytes)
$right_string = $utf8.GetString($right_bytes)

# Detectar las palabras que están mal escritas en cada artículo
# https://www.jesusninoc.com/2018/06/17/detectar-las-palabras-que-estan-mal-escritas-en-un-articulo-de-un-diario-con-un-comando-en-linux-y-ejecutarlo-con-wsl-windows-subsystem-for-linux-desde-powershell/
$xml = [xml]$right_string
$xml.feed.entry.content.'#cdata-section' | %{
    $_
    $_ | bash -c 'aspell list --encoding iso-8859-1 -d es' | Group-Object | Select-Object Name
}

```
