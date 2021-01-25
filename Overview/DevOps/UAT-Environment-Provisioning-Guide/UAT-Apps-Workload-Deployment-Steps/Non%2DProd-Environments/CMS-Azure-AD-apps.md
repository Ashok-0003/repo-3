
#**To upload a self signed certificate follow these steps**
1. Go to the Azure AD app
1. Click on Certificates & Secrets in the right pane
    ![image.png](/.attachments/image-240b8246-62a1-4e8d-848d-badd18d43df4.png)
1. Click on Upload certificate, select .cer file(self signed certificate) and click on Add.
    ![image.png](/.attachments/image-8ea316ad-d02c-4597-a45a-d33edd3973c2.png)


#**To enable API Permissions follow these steps**
1. Go to the Azure AD app
1. Click on API permissions in the right pane
    ![image.png](/.attachments/image-2e593bd0-dc4c-4236-909e-c578c3779185.png)
1. Click on Add a permission, select required permission and click on Add permission.
1. Click on "Grant Admin Consent"

#**There are two Azure AD apps used in CMS**
# 1. spn-cmsbpa-<env>
- CMSBPA certificate to be uploaded, please follow the steps to upload a certificate given above.
- Following permissions should be enabled for this app, please follow the steps to enable API permissions given above. 

|API|Permission name|Type|
|--|--|--|
|Microsoft Graph|GroupMember.Read.All|Application| 
|Microsoft Graph|User.Read|Delegated| 
|Microsoft Graph|User.Read.All|Application|
|Sharepoint|Sites.FullControl.All|Application|
|Sharepoint|Sites.Manage.All|Application| 
|Sharepoint|TermStore.Read.All|Application|   
  ![image.png](/.attachments/image-2852ce21-575e-4976-b2d4-f2346dc1fa0d.png)
# 2. spn-cmsapi-<env>
- CMSAPI certificate to be uploaded, please follow the steps to upload a certificate given above.
- Following permissions should be enabled for this app, please follow the steps to enable API permissions given above. 

|API|Permission name|Type|
|--|--|--|
|Microsoft Graph|User.Read|Delegated| 
|Sharepoint|Sites.Read.All|Application|
|Sharepoint|TermStore.Read.All|Application|
|Sharepoint|User.Read.All|Application|  
  ![image.png](/.attachments/image-9cc120e1-0530-4ed0-8749-1f05da542310.png)