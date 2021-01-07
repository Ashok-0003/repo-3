# URLs per environment:

| Environment| Developer Portal | APIs |Marketplace  |Admin Portal  |My TASMU| Account|
|--|--|--|--|--|--|--|
|sbx|https://apim-cpd-shrd-sbx-we-01.developer.azure-api.net|https://apim-cpd-shrd-sbx-we-01.azure-api.net/config/api/feature |https://sbx-marketplace.tasmu.gov.qa/ |https://sbx-cpadmin.tasmu.gov.qa/ |https://sbx-mytasmu.tasmu.gov.qa/ ||https://sbx-accounts.tasmu.gov.qa/ |
|dev|https://developer.dev.sqcp.qa/|https://api.dev.sqcp.qa/config/api/feature|https://marketplace.dev.sqcp.qa/|https://cpadmin.dev.sqcp.qa/|https://mytasmu.dev.sqcp.qa/|https://account.dev.sqcp.qa/|
|tst|https://developer.tst.sqcp.qa/|https://api.tst.sqcp.qa/config/api/feature|https://marketplace.tst.sqcp.qa/|https://cpadmin.tst.sqcp.qa/|https://mytasmu.tst.sqcp.qa/|https://account.tst.sqcp.qa/|
|tra|https://developer.trn.sqcp.qa/|https://api.trn.sqcp.qa/config/api/feature|https://marketplace.trn.sqcp.qa/|https://cpadmin.trn.sqcp.qa/|https://mytasmu.trn.sqcp.qa/|https://account.trn.sqcp.qa/|
|uat|https://developer.uat.sqcp.qa/|https://api.uat.sqcp.qa/config/api/feature|https://marketplace.uat.sqcp.qa/|https://cpadmin.uat.sqcp.qa/|https://mytasmu.uat.sqcp.qa/|https://account.uat.sqcp.qa/|
For APIs, change the API path accordingly as per ingress path configured


# Debugging Guide
1. Make sure you have the certificate installed and using the correct url. If your API is still not accessible, try below steps:
2. The API swagger.json was updated and the API was deployed to the target environment APIM using APIM pipelines.
3. Go to application gateway acting as an ingress controller (agw-cpd-apps-<env>-we-01) to run a health probe on the API.
- Settings -> Health probes -> Select the matching probe -> Test
- If the communication is not successful, there is some problem with AKS cluster (check steps to debug the cluster)
- If the backend is not healthy, check whether it is APIM or AGIC, test the communication from VM having bastion access (restricted access) using the URLs specific to APIM or AGIC

### AKS Namespaces:
1. apiapps - All Platform APIs
2. webapps - marketplace, adminportal, other web apps
3. jobs - function apps

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
1. Install [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-with-powershell-from-psgallery)
1. Install [chocolatey](https://chocolatey.org/docs/installation#install-with-powershellexe) (to install helm using below command)
1. Install helm 3 (to deploy charts from local)
```
choco install kubernetes-helm
```

Commands to connect to the cluster and debug:
1. Connect to the subscription
```
az login
```
```
az account set --subscription 'Central Platform Development'
```
2. Connect to the cluster
```
az aks get-credentials -g <Resource Group Name> -n <AKS Cluster Name>
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

# Deploy helm charts from local:
Replace the following values in the command:
1. <buildId> - last successful run buildId can be used
2. <chartPath> - give the helm chart path from the machine the command is being executed
3. <releaseName> - specify the release name which is being upgraded
```
helm upgrade --namespace apiapps --install --wait --create-namespace --set image.tag=<buildId>,image.repository=acrcpdglobnpdwe01.azurecr.io/apiapps/<releaseName>,podIdentity=mi-cpd-apps-aks-sbx-we-01,environment.ConnectionStrings__AppConfig=https://acst-cpd-apps-sbx-we-01.azconfig.io <releasename> <chartPath>
```

# Access URLs updated and certificates installed (for sbx env only)

If you want to test or browse the APIs or applications on public network using https. Please follow below steps:
1.	Make the host file entries as below for sbx environment only:
20.54.136.87 sbx-accounts.tasmu.gov.qa
20.54.136.87 sbx-marketplace.tasmu.gov.qa
20.54.136.87 sbx-cpadmin.tasmu.gov.qa
20.54.136.87 sbx-mytasmu.tasmu.gov.qa

2.	Download the certificate - wildcard.tasmu.gov.qa.pfx from [Certs](https://microsofteur.sharepoint.com/:f:/t/TASMUNationalPlatform-DeliveryStream-MicrosoftOnly/EmAB3GrQ2RBLnNB0TS4C6PgBO5_p8E-iFFZPQGv8FYT9lg?e=PkJ84E)
3.	Install the cert using below steps:
a)	Choose store location as local 
b)	Give the path to downloaded pfx
c)	Give password
d)	Specify store as Trusted Root Certification Authority 
e)	Finish