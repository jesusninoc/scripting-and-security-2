# Convert una imagen JPG a caracteres en la consola de PowerShell (obtener el negativo)
## Graphics, PowerShell 
### URL: https://www.jesusninoc.com/2018/01/20/convert-una-imagen-jpg-a-caracteres-en-la-consola-de-powershell-obtener-el-negativo/
```PowerShell
$Cave = [System.Drawing.Bitmap]::FromFile( '.\juan2.jpg' )
$cave
$i=0
$a=0
$array = @()

for ($y = 0;$y -lt $Cave.Height;$y+=1)
{
    for ($x = 0;$x -lt $Cave.Width;$x+=1)
    {
        $col=$Cave.GetPixel($x,$y).Name
        if ($i -lt $Cave.Width -1)
        {
            switch ($col)
            {
                "ff000000" {
                    Write-Host "X" -BackgroundColor Black -ForegroundColor White -NoNewLine
                    $array += "X"
                }
            default{
                Write-Host " " -BackgroundColor white -NoNewLine
                $array += " "
                }
            }
            $i=$i+1
            if ($a -lt 9){$a=$a+1}
            else{$a=0}
        }
        else
        {
            Write-Host " "
            $array += "*"
            $i=0
            $a=0
        }
    }
}

#########
#Negativo
#########
$uu=""
foreach ($p in $array)
{
    if ($p -eq "*")
    {
        write-Host $p -BackgroundColor Black -ForegroundColor White
        $uu=$uu+"`n"
    }
    else
    {
        write-Host $p -BackgroundColor Black -ForegroundColor White -NoNewLine
        $uu=$uu+$p
    }
}

```
