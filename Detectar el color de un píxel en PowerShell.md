# Detectar el color de un píxel en PowerShell
## Graphics, PowerShell 
### URL: https://www.jesusninoc.com/2018/03/06/detectar-el-color-de-un-pixel-en-powershell/
```PowerShell
$GDI = Add-Type -MemberDefinition @'
[DllImport("user32.dll")]
static extern IntPtr GetDC(IntPtr hwnd);

[DllImport("user32.dll")]
static extern Int32 ReleaseDC(IntPtr hwnd, IntPtr hdc);

[DllImport("gdi32.dll")]
static extern uint GetPixel(IntPtr hdc,int nXPos,int nYPos);

static public int GetPixelColor(int x, int y)
{
IntPtr hdc = GetDC(IntPtr.Zero);
uint pixel = GetPixel(hdc, x, y);
ReleaseDC(IntPtr.Zero,hdc);

return (int)pixel;
}
'@ -Name GDI -PassThru

$PixelColorRef = $GDI::GetPixelColor(215,349)
[System.Drawing.Color]::FromArgb($PixelColorRef) | Select-Object B,G,R

```
