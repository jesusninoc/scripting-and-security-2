# Convertir el resultado de la caché DNS a Base64
## Network, PowerShell, Security 
### URL: https://www.jesusninoc.com/2017/10/28/convertir-el-resultado-de-la-cache-dns-a-base64/
```PowerShell
Get-DnsClientCache | %{
[System.Convert]::ToBase64String([System.Text.Encoding]::Unicode.GetBytes($_.Entry))
}

```
