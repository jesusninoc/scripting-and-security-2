# Realizar combinaciones de letras en PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2017/01/09/realizar-combinaciones-de-letras-en-powershell/
```PowerShell
Function Combinaciones
{
  Param(
   [Object[]]$Object,
   [String]$Seperator,
   [UInt32]$CurIndex = 0,
   [String]$Return = ""
  )

  $MaxIndex = $Object.Count - 1
  $Object[$CurIndex] | ForEach-Object {
    [Array]$NewReturn = "$($Return)$($Seperator)$($_)".Trim($Seperator)
    If ($CurIndex -lt $MaxIndex) {
      $NewReturn = Combinaciones $Object -CurIndex ($CurIndex + 1) -Return $NewReturn
    }
    $NewReturn
  }
}

$palabra='abcd'
$arrayletras=@(0..($palabra.Length-1) | % {$palabra[$_]}) #-join ""
$arrayletras

#Combinar cuatro letras distintas en palabras de cuatro letras
#(Combinaciones @($arrayletras,$arrayletras,$arrayletras,$arrayletras)).count
Combinaciones @($arrayletras,$arrayletras,$arrayletras,$arrayletras)

```
