# Conocer el usuario que ejecuta un proceso en un equipo remoto
## PowerShell 
### URL: https://www.jesusninoc.com/2017/09/18/conocer-el-usuario-que-ejecuta-un-proceso-en-un-equipo-remoto/
```PowerShell
$p = Get-WmiObject win32_process -filter "name='explorer.exe'" -ComputerName 192.168.1.56 -Credential (Get-Credential)
$p.getowner().user

```
