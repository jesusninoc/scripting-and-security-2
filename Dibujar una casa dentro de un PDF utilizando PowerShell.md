# Dibujar una casa dentro de un PDF utilizando PowerShell
## Graphics, PowerShell 
### URL: https://www.jesusninoc.com/2017/08/23/dibujar-una-casa-dentro-de-un-pdf-utilizando-powershell/
```PowerShell
#Descargar https://sourceforge.net/projects/itextsharp/

[System.Reflection.Assembly]::LoadFrom("E:\programas\itextsharp-dll-core\itextsharp.dll")

$doc=New-Object itextsharp.text.document
$stream=[IO.File]::OpenWrite("output.pdf")
$writer=[itextsharp.text.pdf.PdfWriter]::GetInstance($doc, $stream)

$doc.Open()

$dc = $writer.DirectContent

#Dibujar un triángulo
$dc.MoveTo(220, 450)
$dc.LineTo(350, 600)
$dc.LineTo(500, 450)
$dc.ClosePathStroke()

#Dibujar un cuadrado
$dc.Rectangle($doc.PageSize.Width-360, 350, 250, 100)
$dc.Stroke();
 
$doc.Close()
$stream.Close()

.\output.pdf

```
