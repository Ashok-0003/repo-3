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
1. The change being promoted is tagged on respective repositories as SIT_ddmmmyyyy (SIT_16Feb2021)
1. Pipelines for pre environment are run from the tags.

## Hotfix Release

- Create release branch from latest stable tag (Eg. SIT_Web_06June2021)
- Follow this naming <Phase>_RC_nn (Eg. RFS_RC_01)
- Cherry pick commits or merge directly on release branch as per the need
- Run CI/CD Pipelines from release branch
- Sanity testing will be done on lower environments (dev,tst,uat) before promoting it to pre/prd (if the changes are for pre/prd only, then it is not required)

## Hotfix Branch Policies - 
1. Minimum Number of Reviewers: 1
1. No direct changes, just cherry picking commits from master
1. Check for comment resolution - REQUIRED
1. Mandatory approvers based on ADO groups like ARM templates approved by DevOps lead, Mobile changes approved by Mobile feature team lead.
