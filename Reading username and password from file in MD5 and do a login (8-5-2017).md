# Reading username and password from file in MD5 and do a login (8-5-2017)
## Cryptography, PowerShell, Security 
### URL: https://www.jesusninoc.com/2017/05/08/reading-username-and-password-from-file-in-md5-and-do-a-login-8-5-2017/
```PowerShell
[Reflection.Assembly]::LoadWithPartialName("System.Web")

#Read user and password
$user=Read-Host
$pass=Read-Host

#Read MD5 file userpass.txt, example content:
#24c9e15e52afc47c225b757e7bee1f9d,4604c8f5d958fea18967bbc7504d0f03 is user1,passwoasdfK$
#Convert user and pass to MD5 and compare

#MD5
$result1=''
$result2=''

$result1 = [System.Web.Security.FormsAuthentication]::HashPasswordForStoringInConfigFile($user, "MD5")
$result2 = [System.Web.Security.FormsAuthentication]::HashPasswordForStoringInConfigFile($pass, "MD5")

Get-Content userpass.txt | % {if(($_.split(",")[0] -like $result1) -and ($_.split(",")[1] -like $result2)){"Login OK"}}

```
