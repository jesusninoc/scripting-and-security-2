# Enviar un vídeo MP4 entre dos Linux mediante Netcat
## Bash, Network 
### URL: https://www.jesusninoc.com/2017/11/12/enviar-un-video-mp4-entre-dos-linux-mediante-netcat/
```Shell
nc -l 8090 < small.mp4

```
```Shell
nc 192.168.1.162 8090 | mplayer -cache 1000 -

```
