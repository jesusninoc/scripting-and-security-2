# Utilizar un filtro LDAP para localizar un usuario
## PowerShell 
### URL: https://www.jesusninoc.com/2018/05/16/utilizar-un-filtro-ldap-para-localizar-un-usuario/
```PowerShell
$SAMAccountName = "jesninoc"
Get-ADUser -LDAPFilter "(samaccountname=$SAMAccountName)"

```
