# Realizar combinaciones de letras utilizando el bucle for en PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2017/01/06/realizar-combinaciones-de-letras-utilizando-el-bucle-for-en-powershell/
```PowerShell
$palabra="abcd"
$arrayletras=@(0..($palabra.Length-1) | % {$palabra[$_]}) #-join ""
for($i=0;$i -lt $arrayletras.Count;$i=$i+1)
{
for($ii=0;$ii -lt $arrayletras.Count;$ii=$ii+1)
{
for($iii=0;$iii -lt $arrayletras.Count;$iii=$iii+1)
{
for($iiii=0;$iiii -lt $arrayletras.Count;$iiii=$iiii+1)
{
$arrayletras[$i]+$arrayletras[$ii]+$arrayletras[$iii]+$arrayletras[$iiii]
}
}
}
}

```
