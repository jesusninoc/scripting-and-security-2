# Encontrar variables en un bloque de PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2017/06/20/encontrar-variables-en-un-bloque-de-powershell/
```PowerShell
$code = {
    $var1 = "Test"
    $var2 = 12
}
$code.Ast.FindAll( { $true }, $true) | Where-Object { $_.GetType().Name -eq 'VariableExpressionAst' } | select variablePath

```
