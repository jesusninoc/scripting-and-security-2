# Utilizar una DLL compilada con Microsoft Visual C# en PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2018/04/17/utilizar-una-dll-compilada-con-microsoft-visual-c-en-powershell/
```PowerShell
[Reflection.Assembly]::LoadFile("C:\Users\juan\Desktop\hola.dll")
[Hola.Hola]::Main()

```
