# Convert bitmap to characters in Write-Host (blue and white)
## Automation, Graphics, PowerShell 
### URL: https://www.jesusninoc.com/2018/01/21/convert-bitmap-to-characters-in-write-host-blue-and-white/
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
#Negative
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

###############
#Blue and white
###############
rm .\traducir2.txt
$ji=0
foreach ($pp in $uu)
{
    if($pp -match "x")
    {
        write-host $ji $pp
        $pp >> traducir2.txt
        $ji=$ji+1
        $valorfinal=$pp.Length
    }
}

```
