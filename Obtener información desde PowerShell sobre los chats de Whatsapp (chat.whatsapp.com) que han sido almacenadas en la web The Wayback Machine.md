# Obtener información desde PowerShell sobre los chats de Whatsapp (chat.whatsapp.com) que han sido almacenadas en la web The Wayback Machine
## PowerShell, Security 
### URL: https://www.jesusninoc.com/2018/05/22/obtener-informacion-desde-powershell-sobre-los-chats-de-whatsapp-chat-whatsapp-com-que-se-han-sido-almacenadas-en-la-web-the-wayback-machine/
```PowerShell
$url = "https://web.archive.org/cdx/search?url=https%3A%2F%2Fchat.whatsapp.com%2F&matchType=prefix&collapse=urlkey&output=json&fl=original%2Cmimetype%2Ctimestamp%2Cendtimestamp%2Cgroupcount%2Cuniqcount&filter=!statuscode%3A%5B45%5D..&limit=100000&_=15336515"
$contenido = (Invoke-WebRequest -Uri $url -UseBasicParsing).Content
$contenido

```
