# Iniciar varios trabajos en segundo plano con PowerShell
## PowerShell, Processes 
### URL: https://www.jesusninoc.com/2018/02/05/iniciar-varios-trabajos-en-segundo-plano-con-powershell/
```PowerShell
#Listar el contenido de directorios
"presentaciones","programas" | %{
    $ScriptBlock = {
        param($name)
        ls $name
    }
    Start-Job $ScriptBlock -ArgumentList $_
}

Get-Job | Receive-Job

```
