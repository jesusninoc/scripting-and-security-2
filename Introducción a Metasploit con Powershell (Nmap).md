# Introducción a Metasploit con Powershell (Nmap)
## PowerShell, Security 
### URL: https://www.jesusninoc.com/2017/01/02/introduccion-a-metasploit-con-powershell-nmap/
```PowerShell
#Realizado por Julián Martínez

#Nmap (Network Mapper) is a security scanner, originally written by Gordon Lyon (also known by his pseudonym Fyodor Vaskovich), used to discover hosts and services on a computer network, thus building a "map" of the network.

#Hacer ping a un rango de direcciones IP con Nmap para detectar las que están usadas por un dispositivo
130..135 | %{nmap -sP 192.168.25.$_}

#Hacer ping con Nmap y saber que sistema operativo tiene el dispositivo de esa IP 
nmap -O 192.168.25.132

```
