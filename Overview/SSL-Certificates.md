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

**Steps to generate PFX**
1. Extract Private Key - openssl pkcs12 -in Certificate.pfx -nocerts -out private.key
2. Validate that Leaf and Intermediates are in Base 64 CRT/CER, else you could do it later by saving it as Base 64 CER
3. Then recreate a PEM/CER Bundle of the entire chain ensuring that they are bundled in the correct order and save to a new bundled.cer. This is done by opening a new notepad/notepad++ file and copying in the contents of the CERTIFICATE (LEAF) and Bundle (Intermediate + Root) into a new file. This new file can be saved as CRT. After saving the file, open the CRT and click on the second tab "Details", then "Copy to File" -- When saving, save as - base 64 encoded CER. 

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



**TASMUPLATFORM.qa**
1. Inform Aissac/SOC, ITSM Team, Yousif/Ops Manager, Platform team, i4s, Crowd Management
2. Replace on NVA
3. Replace on ITSM Servers (Web and App) + App GW, restart IIS services
4. Replace on On Premises Firewall for VPN
5. Replace on Crowd Management - Development Key Vault - kv-crmgn-sec-dev-we-01
6. Testing  - Aisaac inbound testing , VPN check, Crowd Management validation
![image.png](/.attachments/image-bfa9f7c7-5381-49c8-a0f6-34c4458fa8f0.png)
