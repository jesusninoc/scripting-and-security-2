# Convertir a binario las direcciones MAC de todos los dispositivos de red que hay en una red
## Network, PowerShell 
### URL: https://www.jesusninoc.com/2017/01/24/convertir-a-binario-las-direcciones-mac-de-todos-dispositivos-de-red-que-hay-en-una-red/
```PowerShell
ForEach($val in ((Get-NetNeighbor).LinkLayerAddress).replace("-",""))
{
$val
0..($val.Length-1) | %{
Write-Host $val[$_],([Convert]::ToString([Byte]::Parse($val[$_],[System.Globalization.NumberStyles]::HexNumber),2))
}
}

```
