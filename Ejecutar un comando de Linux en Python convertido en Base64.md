# Ejecutar un comando de Linux en Python convertido en Base64
## Bash, Python 
### URL: https://www.jesusninoc.com/2018/02/13/ejecutar-un-comando-de-linux-en-python-convertido-en-base64/
```Python
import os

print "ps".encode('base64','strict');

print "-----"

os.system('cHM='.decode('base64','strict'))

```
