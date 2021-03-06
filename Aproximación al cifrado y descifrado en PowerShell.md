# Aproximación al cifrado y descifrado en PowerShell
## Cryptography, PowerShell, Security 
### URL: https://www.jesusninoc.com/2017/02/23/aproximacion-al-cifrado-y-descifrado-en-powershell/
```PowerShell
##########################################################
#Generar claves para cifrar (convertir las claves en byte)
##########################################################
$clave='clavesecreta123'
$clave2='clavesecreta123'

#Una clave de 128 bits se especifica como un array de byte de 16 dígitos
#Una clave de 192 bits se especifica como un array de byte de 24 dígitos
#Una clave de 256 bits se especifica como un array de byte de 32 dígitos
#A key of 128 bits can be specified as a byte array of 16 digits. Similarly, 192-bit and 256-bit keys correspond to byte arrays of 24 and 32 digits, respectively.
$clavebyteparacifrar=[Byte[]]($clave.PadRight(24).Substring(0,24).ToCharArray())
$clavebyteparadescifrar=[Byte[]]($clave2.PadRight(24).Substring(0,24).ToCharArray())

##########################################################
#Vamos a convertir una cadena segura en una cadena cifrada (convert a secure string to an encrypted string)
##########################################################
#Convertir un texto plano en una cadena segura (convert a plain text string to a secure string)
#ConvertTo-SecureString: Converts encrypted standard strings to secure strings. It can also convert plain text to secure strings. It is used with ConvertFrom-SecureString and Read-Host.
$textoparacifrar=ConvertTo-SecureString "Texto secreto" -AsPlainText -Force
#Otra posibilidad es utilizar Read-Host para introducir un texto para cifrar (create a secure string)
#$textoparacifrar=Read-Host -AsSecureString

#ConvertFrom-SecureString: Converts a secure string to an encrypted standard string
$textocifradoconclave = ConvertFrom-SecureString -SecureString $textoparacifrar -Key $clavebyteparacifrar

##########################################################
#Vamos a convertir una cadena cifrada en una cadena segura (convert an encrypted string to a secure string)
##########################################################
$textoparadescifrar = ConvertTo-SecureString -String $textocifradoconclave -Key $clavebyteparadescifrar

#Extraer el texto plano de la cadena segura (extract password from SecureString)
$textodescifrado=''
$BSTR = [System.Runtime.InteropServices.Marshal]::SecureStringToBSTR($textoparadescifrar)
$textodescifrado = [System.Runtime.InteropServices.Marshal]::PtrToStringAuto($BSTR)
$textodescifrado

```
