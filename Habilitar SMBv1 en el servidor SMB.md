# Habilitar SMBv1 en el servidor SMB
## Filesystem, PowerShell, Security 
### URL: https://www.jesusninoc.com/2017/06/08/habilitar-smbv1-en-el-servidor-smb/
```PowerShell
Set-SmbServerConfiguration -EnableSMB1Protocol $true

```
