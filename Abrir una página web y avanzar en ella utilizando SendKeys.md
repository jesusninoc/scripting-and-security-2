# Abrir una página web y avanzar en ella utilizando SendKeys
## Automation, PowerShell, Web 
### URL: https://www.jesusninoc.com/2016/10/17/abrir-una-pagina-web-y-avanzar-en-ella-utilizando-sendkeys/
```PowerShell
#Abrir una página web, por ejemplo una cuenta de Twitter
Start-Process chrome https://twitter.com/microsoft

#Ir avanzando en la página web mediante la tecla avanzar página
$avanzar=0

do
{
[System.Windows.Forms.SendKeys]::SendWait("{PGDN}")
Start-Sleep -Seconds 5
$avanzar+=1
}while($avanzar -lt 10)

```
