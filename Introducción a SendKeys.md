# Introducción a SendKeys
## Automation, PowerShell 
### URL: https://www.jesusninoc.com/2016/10/10/introduccion-a-sendkeys/
```PowerShell
#Utilice SendKeys para enviar pulsaciones de teclas y combinaciones de teclas a la aplicación activa

#ctrl+esc
[System.Windows.Forms.SendKeys]::SendWait("^({ESC})")

#Notepad
[System.Windows.Forms.SendKeys]::SendWait("notepad")

#Sleep 4 seconds
Start-Sleep -Seconds 4

#ENTER
[System.Windows.Forms.SendKeys]::SendWait("{ENTER}")

```
