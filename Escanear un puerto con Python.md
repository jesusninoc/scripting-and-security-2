# Escanear un puerto con Python
## Network, Python 
### URL: https://www.jesusninoc.com/2017/12/09/escanear-un-puerto-con-python/
```Python
import socket
s=socket.socket(socket.AF_INET, socket.SOCK_STREAM)
result=s.connect_ex(("www.jesusninoc.com",22))
if result == 0:
  print("Puerto abierto")
else:
  print("Puerto no abierto")
  s.close()

```
