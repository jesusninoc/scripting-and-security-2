# Enviar datos a un formulario de Google Docs desde PowerShell (deducir los parámetros que se envían por POST)
## PowerShell 
### URL: https://www.jesusninoc.com/2017/04/30/enviar-datos-a-un-formulario-de-google-docs-desde-powershell-deducir-los-parametros-que-se-envian-por-post/
```PowerShell
$postParams = @{'entry.1383849365'='player1';'entry.215255995'='player2';'entry.902652570'='Cabeza';'entry.929688432'='Piernas'}
$web=Invoke-WebRequest -Uri 'https://docs.google.com/forms/d/e/1FAIpQLSe5xdaYnHpm8vKDnWJkU_dWG7-zsXReJO67Ouhm19F78Ungrw/formResponse' -Method Post -Body $postParams
$web.StatusCode

```
