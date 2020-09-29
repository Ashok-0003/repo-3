Access URLs updated and certificates installed

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