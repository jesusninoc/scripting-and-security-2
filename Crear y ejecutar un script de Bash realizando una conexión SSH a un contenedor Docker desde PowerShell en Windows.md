# Crear y ejecutar un script de Bash realizando una conexión SSH a un contenedor Docker desde PowerShell en Windows
## Bash, PowerShell 
### URL: https://www.jesusninoc.com/2017/10/21/crear-y-ejecutar-un-script-de-bash-realizando-una-conexion-ssh-a-un-contenedor-docker-desde-powershell-en-windows/
```Shell
docker container run -d -p 2222:22 --name test_sshd2 rastasheep/ubuntu-sshd:16.04
docker ps -a

```
```PowerShell
New-SSHSession -ComputerName 192.168.1.36 -Port 2222 -Credential (Get-Credential)
Invoke-SSHCommand -Index 0 'echo "echo hola" > script3.sh'
Invoke-SSHCommand -Index 0 "cat script3.sh"
Invoke-SSHCommand -Index 0 "sh script3.sh"

```
