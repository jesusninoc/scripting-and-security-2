# Recorrer un rango de direcciones IP
## Network, PowerShell 
### URL: https://www.jesusninoc.com/2017/07/14/recorrer-un-rango-de-direcciones-ip/
```PowerShell
foreach($primer in 1..254)
{
    foreach($segundo in 1..254)
    {
        foreach($tercero in 1..254)
        {
            "80."+$primer+"."+$segundo+"."+$tercero
        }
    }
}

```
