# Crear un PDF utilizando PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2017/08/17/crear-un-pdf-utilizando-powershell/
```PowerShell
#Descargar https://sourceforge.net/projects/itextsharp/

[System.Reflection.Assembly]::LoadFrom("E:\programas\itextsharp-dll-core\itextsharp.dll")

$document=New-Object itextsharp.text.document
$stream=[IO.File]::OpenWrite("output.pdf")
[itextsharp.text.pdf.PdfWriter]::GetInstance($document, $stream)

$document.Open()
Get-Content file.txt | %{
$line=New-Object itextsharp.text.Paragraph($_)
$document.Add($line)
}

$document.Close()
$stream.Close()

```
