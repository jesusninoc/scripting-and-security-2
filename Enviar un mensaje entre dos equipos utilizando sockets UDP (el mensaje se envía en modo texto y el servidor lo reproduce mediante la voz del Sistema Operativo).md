# Enviar un mensaje entre dos equipos utilizando sockets UDP (el mensaje se envía en modo texto y el servidor lo reproduce mediante la voz del Sistema Operativo)
## Network, PowerShell 
### URL: https://www.jesusninoc.com/2017/01/28/enviar-un-mensaje-entre-dos-equipos-utilizando-sockets-udp-el-mensaje-se-envia-en-modo-texto-y-el-servidor-lo-reproduce-mediante-la-voz-del-sistema-operativo/
```PowerShell
##Client
$port=2020
$endpoint = new-object System.Net.IPEndPoint ([IPAddress]::Loopback,$port)
$udpclient=new-Object System.Net.Sockets.UdpClient
$b=[Text.Encoding]::ASCII.GetBytes('Hola')
$bytesSent=$udpclient.Send($b,$b.length,$endpoint)
$udpclient.Close()

```
```PowerShell
##Server
$port=2020
$endpoint = new-object System.Net.IPEndPoint ([IPAddress]::Any,$port)
$udpclient=new-Object System.Net.Sockets.UdpClient $port
$content=$udpclient.Receive([ref]$endpoint)
$udpclient.Close()

$sam = New-Object -comObject SAPI.SpVoice
$sam.Speak([Text.Encoding]::ASCII.GetString($content))

```
