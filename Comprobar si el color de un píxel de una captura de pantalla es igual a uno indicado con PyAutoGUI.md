# Comprobar si el color de un píxel de una captura de pantalla es igual a uno indicado con PyAutoGUI
## Automation, Python 
### URL: https://www.jesusninoc.com/2017/12/14/comprobar-si-el-color-de-un-pixel-de-una-captura-de-pantalla-es-igual-a-uno-indicado-con-pyautogui/
```Python
import pyautogui
pyautogui.screenshot()
pyautogui.pixelMatchesColor(50, 200, (255, 255, 238, 255))
pyautogui.pixelMatchesColor(50, 200, (255, 255, 238))

```
