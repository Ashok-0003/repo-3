[[_TOC_]]
#Resolve container image vulnerabilities

1. Navigate to the relevant resource under the 'Unhealthy' section and select the container image you are looking to remediate.
2. Review the set of failed security checks found by the scan, which are sorted from high to low risk.
3. Click on each vulnerability to view its details and explicit remediation instructions and scripts. Check if patches are available to fix the vulnerabilities.
4. Check if vulnerable image is used by pods. If not, goto step 5; else, push new remediated image to your registry and review scan results for the new image to verify the vulnerability no longer exists.

###Steps to check images used by pods

- Connect to the cluster
```
az aks get-credentials -g <Resource Group Name> -n <AKS Cluster Name>
```
- If already connected to a cluster, confirm the name
```
kubectl config current-context
```
- To check image of apiapps and webapps pods. Check this for all environments supported by ACR.
```
kubectl get pods --all-namespaces -o jsonpath="{.items[*].spec.containers[*].image}"

kubectl get pods -n apiapps -o jsonpath="{.items[*].spec.containers[*].image}"
kubectl get pods -n webapps -o jsonpath="{.items[*].spec.containers[*].image}"
```

5. Delete the old image with the vulnerability from your registry. 
To delete old images run script **platform-apis\script\deleteTags.ps1**.

6. After few minutes check ACR security to validate if vulnerability is resolved and removed. 










