# Get RSS feed from jesusninoc.com (new version)
## PowerShell, Web 
### URL: https://www.jesusninoc.com/2018/05/13/get-rss-feed-from-jesusninoc-com-new-version/
```PowerShell
$url = 'https://www.jesusninoc.com/feed/'
(Invoke-RestMethod -Uri $url -UseBasicParsing).title

```
