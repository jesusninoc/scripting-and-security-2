# Recorrer direcciones IP
## Network, PowerShell 
### URL: https://www.jesusninoc.com/2017/07/06/recorrer-direcciones-ip/
```PowerShell
foreach($primer in 1..254)
{
    foreach($segundo in 1..254)
    {
        foreach($tercero in 1..254)
        {
            foreach($cuarto in 1..254)
            {
                ''+$primer+'.'+$segundo+'.'+$tercero+'.'+$cuarto
            }
        }
    }
}

```
