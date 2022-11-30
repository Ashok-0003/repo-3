1. Validate if certificates have purchase validity
2. Validate if certificates have Domain Ownership confirmed, if not - please take the CODE provided within the provider's validation page and create a TXT record in the ROOT domain's DNS zone.
3. For SQCP.QA and TASMUPLATFORM.QA - the public DNS is hosted in Azure. 
4. Certificate provider : Godaddy.com, login is via fmathany@malomatia.com  with 2FA using Authenticator app


Image Reference : ![image.png](/.attachments/image-3770d951-fb2a-469c-805e-64ae70d0306c.png)

Process for renewal

- Identify the areas of use
- Provision the new certificate - PFX
- During Provisioning, validate Root Certificate, Intermediate Certificate and Leaf Certificate
- During Provisioning, validate the expiry dates of each certificate in the chain
- Upload Certificate 
- Test - URLs, SSLlabs for certificate chain review 


**Development, dev.sqcp.qa**
1. Key Vault : Development Subscription : kv-cpd-pltf-dev-we-01 -- Dev-SQCP-Certificate
2. NVA
3. Key Vault : HUB Subscription : kv-cph-pltf-npd-we-01 -- DEV-SQCP-QA


**TASMUPLATFORM.qa**
1. Inform Aissac/SOC, ITSM Team, Yousif/Ops Manager, Platform team, i4s, Crowd Management
2. Replace on NVA
3. Replace on ITSM Servers (Web and App) + App GW, restart IIS services
4. Replace on On Premises Firewall for VPN
5. Replace on Crowd Management - Development Key Vault - kv-crmgn-sec-dev-we-01
6. Testing  - Aisaac inbound testing , VPN check, Crowd Management validation
![image.png](/.attachments/image-bfa9f7c7-5381-49c8-a0f6-34c4458fa8f0.png)



**Steps to generate PFX**
1. Extract Private Key - openssl pkcs12 -in Certificate.pfx -nocerts -out private.key
2. Validate that Leaf and Intermediates are in Base 64 CRT/CER, else you could do it later by saving it as Base 64 CER
3. Then recreate a PEM/CER Bundle of the entire chain ensuring that they are bundled in the correct order and save to a new bundled.crt. This is done by opening a new notepad/notepad++ file and copying in the contents of the CERTIFICATE (LEAF) and Bundle (Intermediate + Root) into a new file. 

-----BEGIN CERTIFICATE-----
(Your Primary SSL certificate: your_domain_name.cer)
-----END CERTIFICATE-----

 -----BEGIN CERTIFICATE-----
(Your Intermediate certificate: DigiCertCA.cer)
-----END CERTIFICATE-----

 -----BEGIN CERTIFICATE-----
(Your Root certificate: TrustedRoot.cer)
-----END CERTIFICATE-----

4. Provision PFX 
openssl pkcs12 -export -out FINALPFX.pfx -inkey privkey.key -in CERTBUNDLE.cer
provide the password for importing private key and exporting PFX
5. Import PFX to both key vaults, run AGW command to set certificate
6. Command
az account set --subscription 'Central Platform Hub'

$AppGw = Get-AzApplicationGateway -Name agw-cph-pltf-ntf-prd-we-01 -ResourceGroupName rg-cph-pltf-edgeagw-prd-we-01
$secret = Get-AzKeyVaultSecret -VaultName "kv-cpp-pltf-prd-we-01" -Name "TASMU-Certificate"
$secretId = $secret.Id.Replace($secret.Version, "9a31bb020e1d454c8b32ccaba41cea3e") # https://kv-cpp-pltf-prd-we-01.vault.azure.net/secrets/
Set-AzApplicationGatewaySslCertificate -ApplicationGateway $AppGW -Name "TASMU-Certificate" -KeyVaultSecretId $secretId


Test, tst.sqcp.qa



Key Vault : Development Subscription : kv-cpd-pltf-tst-we-01 -- Test-SQCP-Certificate
NVA
Key Vault : HUB Subscription : kv-cph-pltf-npd-we-01 -- TST-SQCP-QA
agw-cpd-apps-itsm-tst-we-01 - Manually

On ITSM Server - Tst & Proxy, add certificate manually in IIS and map it to web service