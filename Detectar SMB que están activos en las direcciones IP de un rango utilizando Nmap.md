# Detectar SMB que están activos en las direcciones IP de un rango utilizando Nmap
## Network, PowerShell 
### URL: https://www.jesusninoc.com/2017/08/01/detectar-smb-que-estan-activos-en-las-direcciones-ip-de-un-rango-utilizando-nmap/
```PowerShell
#SMB scripts
#smb2.lua: https://github.com/cldrn/nmap/blob/smbv2/nselib/smb2.lua
#smb.lua: https://github.com/cldrn/nmap/blob/smbv2/nselib/smb.lua
#smb-protocols: https://github.com/cldrn/nmap/blob/smbv2/scripts/smb-protocols.nse
#smb2-capabilities: https://github.com/cldrn/nmap/blob/smbv2/scripts/smb2-capabilities.nse
#smb2-security-mode: https://github.com/cldrn/nmap/blob/smbv2/scripts/smb2-security-mode.nse
#smb2 branch: https://github.com/cldrn/nmap/tree/smbv2

1..254 | %{nmap -p139,445 ('192.168.1.'+$_) --script smb-protocols.nse}

```
