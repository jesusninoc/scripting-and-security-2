# Abrir Safari, hacer clic en una posición del navegador y después cerrarlo
## AppleScript 
### URL: https://www.jesusninoc.com/2016/10/26/abrir-safari-hacer-clic-en-una-posicion-del-navegador-y-despues-cerrarlo/
```AppleScript
tell application "Safari"
	open location "www.jesusninoc.com"
	activate
end tell
delay 10
activate application "Safari"
tell application "System Events"
	tell process "Safari"
		clic at {544, 273}
	end tell
end tell
delay 20
tell application "Safari"
	quit
end tell

```
