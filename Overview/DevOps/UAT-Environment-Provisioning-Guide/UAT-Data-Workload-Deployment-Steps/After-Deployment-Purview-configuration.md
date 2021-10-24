Because the Purview catalog is deployed via DevOps, the owner of this is SPN by default. To add the user account based administrator you need to use Purview REST API. The preferred tool is Postman.
1. Access Bearer token for SPN the Purview has been deployed with.
![image.png](/.attachments/image-1a0091f2-c40a-44e2-8822-87aeb85e5919.png)
1. Copy the access_token and paste it to the authentication bearer and finally request all **metadataPolicies**. 
![image.png](/.attachments/image-11ca29d5-3ac7-45d1-a6da-191e4c050d5e.png)
	After you will get a response, copy the policy Id.
1. With the Policy ID request the metaDataPolicy as below and copy all response. 
![image.png](/.attachments/image-640457d6-9961-4681-95f2-060865ab68be.png)
1. Finally make a PUT request to update policy with new administrator account.
- paste the copied response body from previous step to new PUT request BODY.
- Find the **purviewmetadatarole_buildin_collection_administrator**_**:name of purview instance_**
- Add user Id to the attributeValueIncludedIn node.
- Run the request.
![image.png](/.attachments/image-8d7eb004-e869-4455-ba5b-d640dc37e3f5.png)



