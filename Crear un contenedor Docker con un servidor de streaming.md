# Crear un contenedor Docker con un servidor de streaming
## Bash 
### URL: https://www.jesusninoc.com/2017/11/08/crear-un-contenedor-docker-con-un-servidor-de-streaming/
```Shell
docker pull codeworksio/streaming-server
docker run --detach --restart always \
    --name streaming-server \
    --hostname streaming-server \
    --publish 1935:1935 \
    --publish 8080:8080 \
    --publish 8443:8443 \
    codeworksio/streaming-server

```
```Shell
#Start the streaming server and consumer from the command line
cd ./documents/examples
docker-compose up -d

#Use Open Broadcaster Software to stream your content
#Add media source, e.g. Video Capture Device
#Configure streaming server (Settings > Stream)
#Stream type: Custom Streaming Server
#URL: rtmp://localhost/live
#Stream key: test
#Press Start Streaming button

#Go to http://localhost:9999 URL address in your browser to view the media live.

```
