# Conocer los usuarios que ejecutan procesos en los equipos de una red con PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2017/09/24/conocer-los-usuarios-que-ejecutan-procesos-en-los-equipos-de-una-red-con-powershell/
```PowerShell
$credencial=Get-Credential
1..200 | % {
$ip='192.168.1.'+$_
$p=Get-WmiObject win32_process -filter "name='explorer.exe'" -ComputerName $ip -Credential $credencial
'192.168.1.'+$_,$p.getowner().user
}

```
