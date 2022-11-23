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

- deded