# Ejecutar un ejemplo de reconocimiento de imágenes con TensorFlow realizando una conexión SSH a un contenedor Docker desde PowerShell en Windows
## Bash, PowerShell 
### URL: https://www.jesusninoc.com/2017/10/22/ejecutar-un-ejemplo-de-reconocimiento-de-imagenes-con-tensorflow-realizando-una-conexion-ssh-a-un-contenedor-docker-desde-powershell-en-windows/
```Shell
docker run -it -p 2222:22 gcr.io/tensorflow/tensorflow bash
docker ps -a

```
```PowerShell
#Instalar SSH en un contenedor Docker
apt-get update && apt-get install -y openssh-server
mkdir /var/run/sshd
#El password es toor
echo 'root:toor' | chpasswd
sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd
echo "export VISIBLE=now" >> /etc/profile
#Arrancar sshd
/usr/sbin/sshd -D

```
```PowerShell
New-SSHSession -ComputerName 192.168.1.36 -Port 2222 -Credential (Get-Credential) -Force

#classify_image.py downloads the trained model from tensorflow.org when the program is run for the first time. You'll need about 200M of free space available on your hard disk.
Invoke-SSHCommand -Index 1 'wget https://raw.githubusercontent.com/tensorflow/models/master/tutorials/image/imagenet/classify_image.py'

#Ejecutar el fichero classify_image.py que permite clasificar la imagen (imagen de un oso panda)
$resultado=Invoke-SSHCommand -Index 1 "python classify_image.py"
$resultado.Output

```
