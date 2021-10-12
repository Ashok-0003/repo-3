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
- To check image(tag) of apiapps and webapps pods. Check this for all environments supported by ACR.
```
kubectl get pods --all-namespaces -o jsonpath="{.items[*].spec.containers[*].image}"

kubectl get pods -n apiapps -o jsonpath="{.items[*].spec.containers[*].image}"
kubectl get pods -n webapps -o jsonpath="{.items[*].spec.containers[*].image}"
```

5. Delete the old image(tag) with the vulnerability from your registry. 
You can either manually delete old tags or run script **platform-apis\script\deleteTags.ps1** to perform deletion.
> Don't forget to mention currently used images in $doNotDeleteTags variable in the script.

6. After few minutes check ACR security to validate if vulnerability is resolved and removed. 

##Another method to delete old images(tags)
Only use this command when there are many tags to be deleted or you want to delete tags created before specific time.
This will delete tags from specified repository.

First run this set of commands to check what all images will be purged
```
$PURGE_CMD="acr purge --filter '<repository>:.*' --ago <days> --untagged --dry-run"
az acr run --cmd $PURGE_CMD --registry "<registry_name>" /dev/null'
az acr repository list –-name <registry_name> –-output table
```
After validating, run below sets of commands to purge all the tags created before specific time.
```
# Example:
$PURGE_CMD="acr purge --filter 'apiapps/profileapi:.*' --ago 120d --untagged"
az acr run --cmd $PURGE_CMD --registry "acrcpdglobnpdwe01" /dev/null'
az acr repository list –-name acrcpdglobnpdwe01 –-output table
```








