# Detectar y obtener las coordenadas de todas las veces que aparece un texto en una captura de pantalla con PyAutoGUI
## Automation, Python 
### URL: https://www.jesusninoc.com/2017/12/16/detectar-y-obtener-las-coordenadas-de-todas-las-veces-que-aparece-un-texto-en-una-captura-de-pantalla-con-pyautogui/
```Python
import pyautogui
pyautogui.screenshot()
list(pyautogui.locateAllOnScreen('/Users/lamac/Desktop/detectar.png'))

```
