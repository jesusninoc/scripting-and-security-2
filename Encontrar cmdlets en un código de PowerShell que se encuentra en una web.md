# Encontrar cmdlets en un código de PowerShell que se encuentra en una web
## PowerShell 
### URL: https://www.jesusninoc.com/2018/07/01/encontrar-cmdlets-en-un-codigo-de-powershell-que-se-encuentra-en-una-web/
```PowerShell
$url = "https://www.jesusninoc.com/2017/06/22/encontrar-cmdlets-en-un-bloque-de-powershell/"
$result = Invoke-WebRequest $url
#La etiqueta que tenemos buscar es: class="crayon-plain-wrap"

$code = $result.AllElements | Where Class -eq “crayon-plain-wrap” | %{$_.innerText}

[System.Management.Automation.PSParser]::Tokenize($code,[ref]$null) |
ForEach-Object {
    if ($_.Type -eq 'Command') {
        $_.content
    }
}

```
