# Dibujar varias líneas dentro de un PDF utilizando PowerShell
## Graphics, PowerShell 
### URL: https://www.jesusninoc.com/2017/08/18/dibujar-varias-lineas-dentro-de-un-pdf-utilizando-powershell/
```PowerShell
#Descargar https://sourceforge.net/projects/itextsharp/

[System.Reflection.Assembly]::LoadFrom("E:\programas\itextsharp-dll-core\itextsharp.dll")

$doc=New-Object itextsharp.text.document
$stream=[IO.File]::OpenWrite("output.pdf")
$writer=[itextsharp.text.pdf.PdfWriter]::GetInstance($doc, $stream)

$doc.Open()

$dc = $writer.DirectContent

$dc.MoveTo($doc.PageSize.Width / 2, $doc.PageSize.Height / 2)
$dc.LineTo($doc.PageSize.Width / 2, $doc.PageSize.Height)
$dc.Stroke();
$dc.MoveTo(0, $doc.PageSize.Height/2)
$dc.LineTo($doc.PageSize.Width, $doc.PageSize.Height / 2)
$dc.Stroke()

$doc.Close()
$stream.Close()

```
