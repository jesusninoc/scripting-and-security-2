# Hackear wifi con PowerShell (script en una línea)
## PowerShell, Security, Wireless 
### URL: https://www.jesusninoc.com/2017/01/31/hackear-wifi-con-powershell-script-en-una-linea/
```PowerShell
(netsh wlan show interface | Select-String SSID)[0] | %{[String]$SSID=$_;$SSID=$SSID.replace("SSID","").replace(":","").trim();$SSID;netsh wlan show profile name=$SSID key=clear | Select-String 'Contenido de la clave';}

```
