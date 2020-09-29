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
1. Make sure you have the certificate installed and using the correct url. If your API is still not accessible, try below steps:
2. The API swagger.json was updated and the API was deployed to the target environment APIM using APIM pipelines.
3. Go to application gateway acting as an ingress controller (agw-cpd-apps-<env>-we-01) to run a health probe on the API.
- Settings -> Health probes -> Select the matching probe -> Test
- If the communication is not successful, there is some problem with AKS cluster (check steps to debug the cluster)
- If the communication is successful, for dev, tst, tra, run the health probes on external application gateway - agw-cph-apps-temp-we-01
 (having restricted access) for the respective backend
- If the backend is not healthy, check whether it is APIM or AGIC, test the communication from VM having bastion access (restricted access) using the URLs specific to APIM or AGIC

### AKS Namespaces:
1. apiapps - All Platform APIs
2. webapps - marketplace, adminportal, other web apps
3. jobs - functions

## AKS Cluster
### Using portal UI
1. Go to the environment specific cluster - aks-cpd-apps-<env>-we-01
Monitoring -> Insights -> Containers
- Select the relevant container
- Check if the deployed image is latest or matched with the build Id
- Select view in analytics and view kubernetes event logs

2. For public clusters, kubernetes resources pane gives good view on workloads
 Cluster -> Kubernetes Resources -> Deployments, Jobs

### Using command line
Pre requisites to run these from local system:
1. Install [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli) 
2. Install [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-with-powershell-from-psgallery)

Commands:
1. Connect to the subscription
```
az account get-access-token --subscription 'Central Platform Development'
```
2. Connect to the cluster
```
az aks get-credentials -g rg-cpd-apps-sbx-we-01 -n aks-cpd-apps-sbx-we-01
```
3. If already connected to a cluster, confirm the name
```
kubectl config current-context
```
4. To monitor a specific pod
```
kubectl get pods -n <namespace>
```
5. Copy the pod name and then fetch logs
```
kubectl logs pod/<podname> -n <namespace>
```
6. To get the other details about pod image/events
```
kubectl describe pod/<podname> -n <namespace>
```
7. Get events from a namespace
```
kubectl get events -n <namespace> 
```
8. For more debugging, follow this [link](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)