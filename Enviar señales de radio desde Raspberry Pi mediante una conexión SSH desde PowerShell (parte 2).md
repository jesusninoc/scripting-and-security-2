# Enviar señales de radio desde Raspberry Pi mediante una conexión SSH desde PowerShell (parte 2)
## PowerShell, Radio 
### URL: https://www.jesusninoc.com/2018/02/22/enviar-senales-de-radio-desde-raspberry-pi-mediante-una-conexion-ssh-desde-powershell-parte-2/
```PowerShell
#Subir el audio a Raspberry Pi realizando una conexión SCP

#Iniciar una sesión SCP
#Para iniciar sesión SSH es necesario indicar la dirección IP del equipo al que nos vamos a conectar y también hay que introducir los credenciales (usuario y contraseña).

$Pass = ConvertTo-SecureString -String "raspberry" -AsPlainText -Force
$Credential = New-Object -TypeName "System.Management.Automation.PSCredential" -ArgumentList "pi", $Pass

#Para configurar Set-SCPFile
#Indicar el fichero que vamos a subir -LocalFile
#Indicar el equipo al que nos vamos a conectar -ComputerName
#Indicar la ruta en la que vamos a subir el audio -RemotePath
#Forzar la conexión para evitar fallo "Key exchange negotiation failed."
#Indicar los credenciales que hemos creado anteriormente

Set-SCPFile -LocalFile .\saludo.wav -ComputerName 192.168.1.161 -RemotePath ./fmm/fm_transmitter-master -Force -Credential $Credential

```
