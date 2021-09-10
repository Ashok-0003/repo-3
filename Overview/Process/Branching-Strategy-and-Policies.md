# [Trunk Based Development Strategy](https://trunkbaseddevelopment.com)

- Short lived branches
- Recommended lifetime: 2-10 days
- Branch naming convention - <developername>/<UserStoryID/WorkItemId>
- PRs to be raised against master branch

![image.png](/.attachments/image-a49e2356-66d1-4521-9577-c0b2aadff9e5.png)

## Branch Policies for master
1. Minimum Number of Reviewers: 1.
1. Users cant approve their own changes.
1. Check for linked work items – REQUIRED.
1. Check for Comment Resolution – REQUIRED.
1. Squash Merge.
1. Mandatory approvers based on ADO groups like ARM templates approved by DevOps lead, Mobile changes approved by Mobile feature team lead.

## Pull Request
1. Developer will raise a pull request for the master branch only.
1. Work Item association is MUST for the pull request.
1. CI Build validation should pass before the code is merged into master branch.
1. Delete the branch after merge 

## SIT Release
1. The change being promoted is tagged on respective repositories as SIT_<Component>_ddmmmyyyy (Eg.SIT_APIM_16Feb2021)
1. Pipelines for pre environment are run from the tags.

## Hotfix Release

- Create release branch from latest stable tag (Eg. SIT_Web_06Jun2021)
- Follow this naming Hotfix/<Phase>_<Component>_ddmmmyyyy (Eg. Hotfix/RFS_Web_16Jun2021)
- Apply policies mentioned below on the hotflix branch
- Cherry pick commits on release branch and raise PR to add the changes
- Run CI/CD Pipelines from release branch
- Sanity testing will be done on lower environments (dev,tst,uat) before promoting it to pre/prd (if the changes are for pre/prd only, then it is not required)

## Hotfix Branch Policies - 
1. Minimum Number of Reviewers: 1
1. No direct changes, just cherry picking commits from master
1. Check for comment resolution - REQUIRED
1. Mandatory approvers based on ADO groups like ARM templates approved by DevOps lead, Mobile changes approved by Mobile feature team lead.

## CRM Configurations/Solutions Hotfix
- Solution patching can be used for CRM configuration hotfixes whenever the complete build deployment or complete solution(s) deployments cannot be done. More details on how to create patch solutions is documented [here](https://docs.microsoft.com/en-us/power-platform/alm/create-patches-simplify-solution-updates).
- Follow the steps below to prepare the hotfix.
  - Identify the components which needs to be deployed. There are two options depending on the components. Either identify one or more of the existing solutions which contains the changes to be deployed in the hotfix, if that's not possible, create small patch solutions based on existing solutions.
  - The patch solution would contain only the changes required to be deployed in the hotfix.
  - The CD pipeline [CD-CrmPlatform-Hotfix](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=1597) will be used whenever a hotfix needs to be deployed with any specific solution(s) or solution patches. The solution(s) or solution patches for the specific hotfix release needs to be updated in the aforementioned pipeline.
  - Then follow the usual deployment process of promoting the same pipeline to each environment.

## CMS Hotfix
- SPO Patch updates will be performed through pipeline, CD  SPO patch Update, which will execute the PowerShell(.ps) patch file.Main Script as well should be updated for these patch updates.

## WebApps Hotfix

1. For the web-apps repository, create a branch from the last production deployment commit/Tag/Branch. Name it as Hotfix/web-apps-rfs-<DDMMMYYYY>
2. Merge all the files(changes) that are for the hotfix into this branch.
a. Update the package version of all the libraries to next minor version e.g. 1.0.0 should be updated to 1.1.0
3. Build the CI pipeline (from the branch) to verify the merging is proper.
4. Change the file get-publishchange-queue.ps1 under /pipeline/build/templates as below:
![image.png](/.attachments/image-61c86fb3-7ef6-4cff-adb5-65439a6f65a5.png)
5. Run CI-Webapps-Npm to publish the library changes to artifacts.
6. Run CD-Webapp-Release to deploy to DEV, TEST and UAT.
7. Then, Run CD-Webapps-prd-Release to deploy to pre-prod and prod environment.
