# Downdetector with PowerShell
## PowerShell, Servers 
### URL: https://www.jesusninoc.com/2017/07/01/downdetector-with-powershell/
```PowerShell
using assembly System.Windows.Forms
using namespace System.Windows.Forms
 
function screenshot($path)
{
    Start-Process chrome "https://downdetector.com/status/level3/map/"
    Start-Sleep -Seconds 5
	$b=New-Object System.Drawing.Bitmap([System.Windows.Forms.Screen]::PrimaryScreen.Bounds.Width, [System.Windows.Forms.Screen]::PrimaryScreen.Bounds.Height)
	$g=[System.Drawing.Graphics]::FromImage($b)
	$g.CopyFromScreen((New-Object System.Drawing.Point(0,0)), (New-Object System.Drawing.Point(0,0)), $b.Size)
	$g.Dispose()
	$b.Save($path,'Bmp')
}

$form = [Form] @{
Text = 'Mi formulario'
BackgroundImageLayout = "None"
}
#Creación de los botones
$button = [Button] @{
 Text = 'Level3'
 Dock = 'Top'
}

#Acciones de los botones
$button.add_Click{

screenshot(".\test.bmp")

#Creación del formulario
$Image=[system.drawing.image]::FromFile(".\test.bmp")

$form2 = [Form] @{
Text = 'Mi formulario'
BackgroundImage = $Image
Width = $Image.Width
Height = $Image.Height
BackgroundImageLayout = "None"
}
$form2.ShowDialog()
}

#Añadir botones al formulario
$form.Controls.Add($button)
$form.ShowDialog()

```
