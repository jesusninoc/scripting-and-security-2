# Script para generar diccionarios para realizar fuerza bruta para SHA1 con PowerShell
## Cryptography, PowerShell, Security 
### URL: https://www.jesusninoc.com/2016/12/23/script-para-generar-diccionarios-para-realizar-fuerza-bruta-para-sha1-con-powershell/
```PowerShell
[Reflection.Assembly]::LoadWithPartialName("System.Web")

gc .\diccionario.txt | %{
$_+","+([System.Web.Security.FormsAuthentication]::HashPasswordForStoringInConfigFile($_, "SHA1")) | Out-File -Append diccionariofuerza.txt
}

```
```PowerShell
[Reflection.Assembly]::LoadWithPartialName("System.Web")
#Listar letras de la a a la z
[Char]'a'..[Char]'z' | %{
[Char]$_+","+([System.Web.Security.FormsAuthentication]::HashPasswordForStoringInConfigFile([Char]$_, "SHA1")) | Out-File -Append diccionariofuerza.txt
}

```
```PowerShell
[Reflection.Assembly]::LoadWithPartialName("System.Web")
#Listar letras de la A a la Z
[Char]'A'..[Char]'Z' | %{
[Char]$_+","+([System.Web.Security.FormsAuthentication]::HashPasswordForStoringInConfigFile([Char]$_, "SHA1")) | Out-File -Append diccionariofuerza.txt
}

```
