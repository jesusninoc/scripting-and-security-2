# Encontrar cmdlets y variables en un bloque de PowerShell
## PowerShell, Security 
### URL: https://www.jesusninoc.com/2017/10/18/encontrar-cmdlets-y-variables-en-un-bloque-de-powershell/
```PowerShell
$code = {
    Get-Process
    Get-Service
    $var2 = 12
}
$code.Ast.FindAll( { $true }, $true) | Where-Object { $_.GetType().Name -eq 'CommandAst' } | select CommandElements
$code.Ast.FindAll( { $true }, $true) | Where-Object { $_.GetType().Name -eq 'VariableExpressionAst' } | select variablePath

```
