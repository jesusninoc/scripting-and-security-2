# Estado actual de la configuración del protocolo del servidor SMB
## Filesystem, PowerShell, Security 
### URL: https://www.jesusninoc.com/2017/06/02/estado-actual-de-la-configuracion-del-protocolo-del-servidor-smb/
```PowerShell
Get-SmbServerConfiguration | Select EnableSMB1Protocol, EnableSMB2Protocol

```
