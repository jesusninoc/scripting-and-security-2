# Programación Movistar+ con PowerShell
## Automation, PowerShell 
### URL: https://www.jesusninoc.com/2017/10/12/programacion-movistar-con-powershell/
```PowerShell
$json=(Invoke-WebRequest -Uri 'http://akamaicache.dof6.com/vod/yomvi.svc/samsung_tizen/profiles/OTT/channels?parentalRating=M18&showNonRated=true').content | ConvertFrom-JSON
$json | select Nombre,@{Name="Titulo";Expression={$_.pases.titulo}} | Out-GridView

```
