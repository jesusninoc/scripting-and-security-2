# View all the Euribor rates available
## PowerShell, Web scraping 
### URL: https://www.jesusninoc.com/2016/12/20/view-all-the-euribor-rates-available/
```PowerShell
$web=Invoke-WebRequest 'https://www.emmi-benchmarks.eu/euribor-org/about-euribor.html'
$web.AllElements | Where class -eq “box_inner” | %{$_.innerText}

```
