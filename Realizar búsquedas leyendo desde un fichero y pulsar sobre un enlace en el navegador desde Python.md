# Realizar búsquedas leyendo desde un fichero y pulsar sobre un enlace en el navegador desde Python
## Automation, Python, Web 
### URL: https://www.jesusninoc.com/2018/02/01/realizar-busquedas-leyendo-desde-un-fichero-y-pulsar-sobre-un-enlace-en-el-navegador-desde-python/
```Python
import time
from selenium import webdriver

infile = open('palabras.txt', 'r')
for line in infile:
   driver = webdriver.Chrome()
   driver.get('http://www.google.com');
   search_box = driver.find_element_by_name('q')
   search_box.send_keys(line)
   search_box = driver.find_element_by_name('q').send_keys(u'\ue007')
   findElem = driver.find_element_by_link_text('Welcome to Python.org')
   findElem.click()
   time.sleep(5)
   driver.quit()
infile.close()

```
