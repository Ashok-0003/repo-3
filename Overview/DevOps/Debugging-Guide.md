# Access URLs updated and certificates installed

If you want to test or browse the APIs or applications on public network using https. Please follow below steps:
1.	Make the host file entries as below:
20.54.136.87 dev-api.tasmu.gov.qa
20.54.136.87 dev-accounts.tasmu.gov.qa
20.54.136.87 dev-marketplace.tasmu.gov.qa
20.54.136.87 dev-cpadmin.tasmu.gov.qa
20.54.136.87 tst-api.tasmu.gov.qa
20.54.136.87 tst-accounts.tasmu.gov.qa
20.54.136.87 tst-marketplace.tasmu.gov.qa
20.54.136.87 tst-cpadmin.tasmu.gov.qa
20.54.136.87 tra-api.tasmu.gov.qa
20.54.136.87 tra-accounts.tasmu.gov.qa
20.54.136.87 tra-marketplace.tasmu.gov.qa
20.54.136.87 tra-cpadmin.tasmu.gov.qa
2.	Download the certificate - wildcard.tasmu.gov.qa.pfx from [Certs](https://microsofteur.sharepoint.com/:f:/t/TASMUNationalPlatform-DeliveryStream-MicrosoftOnly/EmAB3GrQ2RBLnNB0TS4C6PgBO5_p8E-iFFZPQGv8FYT9lg?e=PkJ84E)
3.	Install the cert using below steps:
a)	Choose store location as local 
b)	Give the path to downloaded pfx
c)	Give password
d)	Specify store as Trusted Root Certification Authority 
e)	Finish

URLs per environment:

| Environment | APIs |Marketplace  |Admin Portal  |
|--|--|--|--|
|sbx|https://apim-cpd-shared-sbx-we-01.azure-api.net/config/api/feature | | |
|dev|https://dev-api.tasmu.gov.qa/config/api/feature|https://dev-marketplace.tasmu.gov.qa/|https://dev-cpadmin.tasmu.gov.qa/|
|tst|https://tst-api.tasmu.gov.qa/config/api/feature|https://tst-marketplace.tasmu.gov.qa/|https://tst-cpadmin.tasmu.gov.qa/|
|tra|https://tra-api.tasmu.gov.qa/config/api/feature|https://tra-marketplace.tasmu.gov.qa/|https://tra-cpadmin.tasmu.gov.qa/|
For APIs, change the API path accordingly as per ingress path configured


# Debugging Guide
1. Please make sure if you have the certificate installed and using the correct url. If your API is still not accessible, try below steps:
2. The API swagger.json was updated and the API was deployed to the target environment APIM using APIM pipelines.
3. Go to application gateway acting as an ingress controller (agw-cpd-apps-<env>-we-01) to run a health probe on the API.
- Settings -> Health probes -> Select the matching probe -> Test
- If the communication is not successful, there is some problem with AKS cluster
- If the communication is successful, for dev, tst, tra, run the health probes on external application gateway - agw-cph-apps-temp-we-01
 (having restricted access) for the respective backend
- If the backend is not healthy, check whether it is APIM or AGIC, test the communication from VM having bastion access (restricted access) using the URLs specific to APIM or AGIC

4. 