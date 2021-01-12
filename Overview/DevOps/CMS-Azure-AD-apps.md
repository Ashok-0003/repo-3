**Here are the deployment details of CMS Azure AD apps**
**To upload a self signed certificate follow these steps**
1. Go to the Azure AD app
1. Click on Certificates & Secrets in the right pane
    ![image.png](/.attachments/image-1ef4d219-cf0c-4671-a6fa-4edb559104ca.png)
1. Click on Upload certificate, select .cer file(self signed certificate) and click on Add.
    ![image.png](/.attachments/image-51386c4d-01f9-4152-90e1-33b0d9330a66.png)


**To enable API Permissions follow these steps**
1. Go to the Azure AD app
1. Click on API permissions in the right pane
    ![image.png](/.attachments/image-89eccc7b-9e93-47cf-b58c-a7d549aa9954.png)
1. Click on Add a permission, select required permission and click on Add permission.

**There are two Azure AD apps used in CMS**
# 1. spn-cmsbpa-<env>
- Following permissions should be enabled for this app 
  ![image.png](/.attachments/image-05e42f7e-9317-4b72-8b99-c1729a722f8d.png)
# 2. spn-cmsapi-<env>
- Following permissions should be enabled for this app 
  ![image.png](/.attachments/image-48967237-4ffc-44cf-88a0-1b6ca1925515.png)