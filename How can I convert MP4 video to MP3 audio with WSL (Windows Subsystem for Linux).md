# How can I convert MP4 video to MP3 audio with WSL (Windows Subsystem for Linux)
## Bash, PowerShell 
### URL: https://www.jesusninoc.com/2018/06/02/how-can-i-convert-mp4-video-to-mp3-audio-with-wsl-windows-subsystem-for-linux/
```PowerShell
bash -c 'ffmpeg -i fich.mp4 -acodec libmp3lame audio.mp3'

```
