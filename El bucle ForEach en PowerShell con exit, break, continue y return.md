# El bucle ForEach en PowerShell con exit, break, continue y return
## PowerShell 
### URL: https://www.jesusninoc.com/2018/05/14/el-bucle-foreach-en-powershell-con-exit-break-continue-y-return/
```PowerShell
# El ForEach se ejecuta normal
1..5 | %{
    $_
}

```
```PowerShell
# Se detiene TODO y sale del ámbito
# Muestra 1 y sale de TODO
1..5 | %{
    if($_ -eq 2){exit;$_;}
    else{$_}
}

```
```PowerShell
# Sale del bucle
# Muestra 1 y sale del bucle
1..5 | %{
    if($_ -eq 2){break;$_}
    else{$_}
}

```
```PowerShell
# Sale del bucle
# Muestra 1 y sale del bucle
1..5 | %{
    if($_ -eq 2){continue;$_}
    else{$_}
}

```
```PowerShell
# Devuelve el control al bucle para pueda continuar
# Muestra 1 3 4 y 5
1..5 | %{
    if($_ -eq 2){return;$_}
    else{$_}
}

```
