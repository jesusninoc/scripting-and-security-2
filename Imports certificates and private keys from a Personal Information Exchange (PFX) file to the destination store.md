# Imports certificates and private keys from a Personal Information Exchange (PFX) file to the destination store
## Cryptography, PowerShell, Security 
### URL: https://www.jesusninoc.com/2017/11/20/imports-certificates-and-private-keys-from-a-personal-information-exchange-pfx-file-to-the-destination-store/
```PowerShell
#Imports certificates and private keys from a Personal Information Exchange (PFX) file to the destination store
Import-PfxCertificate .\cert.pfx -CertStoreLocation "Cert:\CurrentUser\My" -Password $Password

#Decrypts content that has been encrypted by using the Cryptographic Message Syntax format
Unprotect-CmsMessage -Path secret.txt

```
