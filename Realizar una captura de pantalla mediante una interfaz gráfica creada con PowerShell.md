# Realizar una captura de pantalla mediante una interfaz gráfica creada con PowerShell
## Graphics, PowerShell 
### URL: https://www.jesusninoc.com/2016/12/08/realizar-una-captura-de-pantalla-mediante-una-interfaz-grafica-creada-con-powershell/
```PowerShell
#Realizado por Jesús Moreno

[Reflection.Assembly]::LoadWithPartialName("System.Drawing")
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

function screenshot($path)
{
	$b=New-Object System.Drawing.Bitmap([System.Windows.Forms.Screen]::PrimaryScreen.Bounds.Width, [System.Windows.Forms.Screen]::PrimaryScreen.Bounds.Height)
	$g=[System.Drawing.Graphics]::FromImage($b)
	$g.CopyFromScreen((New-Object System.Drawing.Point(0,0)), (New-Object System.Drawing.Point(0,0)), $b.Size)
	$g.Dispose()
	$b.Save($path,'Bmp')
}

$form = New-Object System.Windows.Forms.Form 
$form.Text = "Guardar fondo"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "Guardar"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancelar"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Nombre para guardar la foto:"
$form.Controls.Add($label) 

$textBox = New-Object System.Windows.Forms.TextBox 
$textBox.Location = New-Object System.Drawing.Point(10,40) 
$textBox.Size = New-Object System.Drawing.Size(260,20) 
$form.Controls.Add($textBox) 

$form.Topmost = $True

$form.Add_Shown({$textBox.Select()})
$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
Start-Sleep -Seconds 1
$x = $textBox.Text
$path= "$HOME\Desktop\$x.bmp"
screenshot($path)
}

```
