# Ejecutar Microsoft COFF Binary File Dumper (DUMPBIN.EXE) desde PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2018/04/15/ejecutar-microsoft-coff-binary-file-dumper-dumpbin-exe-desde-powershell/
```PowerShell
# Información sobre Microsoft COFF Binary File Dumper DUMPBIN
# https://msdn.microsoft.com/es-es/library/c1h23y6c.aspx

cd "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Tools\MSVC\14.13.26128\bin\Hostx86\x86"
.\dumpbin.exe /exports C:\Windows\System32\zipfldr.dll

```
