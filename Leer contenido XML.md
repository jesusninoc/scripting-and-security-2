# Leer contenido XML
## PowerShell, Web 
### URL: https://www.jesusninoc.com/2017/02/20/leer-contenido-xml/
```PowerShell
([xml] [System.Net.WebClient]::new().
 DownloadString('https://blogs.msdn.com/powershell/rss.aspx')).
 RSS.Channel.Item |
 Format-Table title,link

```
