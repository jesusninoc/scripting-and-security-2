# Exports a certificate to a Personal Information Exchange (PFX) file
## Cryptography, PowerShell, Security 
### URL: https://www.jesusninoc.com/2017/11/18/exports-a-certificate-to-a-personal-information-exchange-pfx-file/
```PowerShell
#Creates a new self-signed certificate
$cert = New-SelfSignedCertificate -DnsName jesusninoc -CertStoreLocation "Cert:\CurrentUser\My" -KeyUsage KeyEncipherment,DataEncipherment, KeyAgreement -Type DocumentEncryptionCert  -KeyExportPolicy ExportableEncrypted

#Encrypts content by using the Cryptographic Message Syntax format
"Hello" | Protect-CmsMessage -To cn=jesusninoc -OutFile secret.txt

#Decrypts content that has been encrypted by using the Cryptographic Message Syntax format
Unprotect-CmsMessage -Path secret.txt

#Exports a certificate to a Personal Information Exchange (PFX) file
$Password = Read-Host -Prompt 'Password to protect certificate' -AsSecureString
$cert | Export-PfxCertificate -Password $Password -FilePath cert.pfx

```
