# Detectar las palabras que están mal escritas en un texto con un comando en Linux y ejecutarlo con WSL (Windows Subsystem for Linux) desde PowerShell
## Bash, PowerShell 
### URL: https://www.jesusninoc.com/2018/06/11/detectar-las-palabras-que-estan-mal-escritas-en-un-texto-con-un-comando-en-linux-y-ejecutarlo-con-wsl-windows-subsystem-for-linux-desde-powershell/
```PowerShell
gc .\corregir.txt | bash -c 'aspell list --encoding utf-8 -d es'

```
