# Ejecutar Airodump-ng en Linux realizando una conexión SSH desde PowerShell en Windows
## PowerShell, Wireless 
### URL: https://www.jesusninoc.com/2017/10/14/ejecutar-airodump-ng-en-linux-realizando-una-conexion-ssh-desde-powershell-en-windows/
```PowerShell
$sUser = "ubuntu"
$oSessionSSH = New-SSHSession -ComputerName 192.168.1.163 -Credential $credencial

#Crear canal de comunicación entre PowerShell y Linux
#Convertirse en sudo para ejecutar Airodump-ng
$stream = $oSessionSSH.Session.CreateShellStream("PS-SSH", 0, 0, 0, 0, 1000)
Invoke-SSHStreamExpectSecureAction -ShellStream $stream -Command "sudo su -" -ExpectString "[sudo] password for $($sUser):"
Start-Sleep -Seconds 5
$stream.Read()
$stream.WriteLine("airodump-ng wlp2s0mon -w resultado")
$stream.Read()
Start-Sleep -Seconds 5

#Finalizar la ejecución de Airodump-ng
$stream.WriteLine([char]26)
$stream.Read()

#Abrir el fichero CSV con la información sobre las redes inalámbricas
$commando = "cat resultado-01.csv"
$stream.WriteLine($commando)
Start-Sleep -Seconds 5
$ssid=$stream.Read()
Start-Sleep -Seconds 5
$ssid

```
