# United States Department of Agriculture Food Composition Databases with PowerShell
## PowerShell 
### URL: https://www.jesusninoc.com/2018/03/14/united-states-department-of-agriculture-food-composition-databases-with-powershell/
```PowerShell
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
$web = Invoke-WebRequest "https://ndb.nal.usda.gov/ndb/foods/show/85167"
$usda = ($web.AllElements | Where id -eq “nutdata").innerhtml | %{
    $_ -replace "<TD class=cspan>","#" -replace "</TR>","#" -replace "</TD>","|" -replace "<.*?>" -split "`n"  -join "" | ? {$_.trim() -ne ""}
}

$productos = @{}

$usda.split("#") -split "`n" | ? {$_.trim() -ne ""} | %{
    $productos.Add($_.split("|")[1].trim(),$_.split("|")[4].trim())
}

$productos.GetEnumerator()

```
