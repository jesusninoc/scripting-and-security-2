# Deshabilitar UAC desde PowerShell
## PowerShell, Registry 
### URL: https://www.jesusninoc.com/2018/01/15/deshabilitar-uac-desde-powershell/
```PowerShell
cd HKLM:\
$RegKey ='HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\policies\system'
Set-ItemProperty -Path $RegKey -Name EnableLUA -Value 0

```
