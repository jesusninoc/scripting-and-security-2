# Extraer las palabras de un texto mediante Aspell de Linux desde PowerShell con WSL
## Bash, PowerShell 
### URL: https://www.jesusninoc.com/2018/06/20/extraer-las-palabras-de-un-texto-mediante-aspell-de-linux-desde-powershell-con-wsl/
```PowerShell
(gc .\corregir.txt).Split(" ").ToLower() | bash -c 'aspell list --encoding iso-8859-1' | Group-Object | Sort-Object Count,Name

```
