# Mover el ratón con duración a varias posiciones de la pantalla con PyAutoGUI
## Automation, Python 
### URL: https://www.jesusninoc.com/2017/11/25/mover-el-raton-con-duracion-a-varias-posiciones-de-la-pantalla-con-pyautogui/
```Python
import pyautogui
for i in range(5):
  pyautogui.moveTo(100, 100, duration=0.25)
  pyautogui.moveTo(200, 100, duration=0.25)

```
