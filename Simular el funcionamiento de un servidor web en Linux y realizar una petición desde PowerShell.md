# Simular el funcionamiento de un servidor web en Linux y realizar una petición desde PowerShell
## Bash, Network, PowerShell, Servers 
### URL: https://www.jesusninoc.com/2017/11/16/simular-el-funcionamiento-de-un-servidor-web-en-linux-y-realizar-una-peticion-desde-powershell/
```Shell
echo '<html><title>hola</title></html>' | nc -l -p 99 -q 1

```
```PowerShell
$IE= new-object -com InternetExplorer.Application
$IE.navigate2("http://192.168.1.162")

while ($IE.busy) {
sleep -milliseconds 100
}

$IE.visible=$true

```
