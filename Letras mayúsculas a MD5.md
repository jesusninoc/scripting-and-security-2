# Letras mayúsculas a MD5
## Cryptography, PowerShell, Security 
### URL: https://www.jesusninoc.com/2017/01/24/letras-mayusculas-a-md5/
```PowerShell
[Reflection.Assembly]::LoadWithPartialName("System.Web")
#Listar letras de la A a la Z
[char]'A'..[char]'Z' | %{
#ASCII code to MD5
[System.Web.Security.FormsAuthentication]::HashPasswordForStoringInConfigFile([char]$_, "MD5")
}

```
