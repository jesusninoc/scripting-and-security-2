# Enviar un formulario de contacto de WordPress desde PowerShell
## PowerShell, Web, Web scraping 
### URL: https://www.jesusninoc.com/2017/10/10/enviar-un-formulario-de-contacto-de-wordpress-desde-powershell/
```PowerShell
$postParams = @{'your-name'='name';'your-email'='email@email.com';'your-message'='message';}
Invoke-WebRequest -Uri "https://www.jesusninoc.com/wp-json/contact-form-7/v1/contact-forms/34/feedback" -Method POST -Body $postParams

```
