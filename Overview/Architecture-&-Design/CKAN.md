**Resource uploading process:**
Below image depicts the file (resource) uploading process.
![image.png](/.attachments/image-405936f4-3dc9-40c0-bc11-451e9c9ad0f3.png)

1. Admin will place the file in storage account under CKAN container.
2. Open Purview resource and scan the data lake one which has the above storage account as the source.
3. Logic App will run once in day. this will process the file. Logic app code is present in infra code base and can be seen in the portal as well.
4. It first fetches the file details and then gets the metadata from Purview.
5. It creates a package (dataset) using rest api. the dataset can be seen in Open data portal.
6. then the logic app will upload the file to azure function app.
7. the function app will upload the file to front portal using rest api. this code is present in the platform api and the solution is: CkanResourceCreationFunction
 
**For more information and visual representation, Recordings of the KT will be helpful.**

**Data Pusher:**
- Please refer to [Open data deployment wiki](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/627/Opendata-Portal-Deployment) for the setup and commands to use
- Data pusher will support tabular formats. like csv,tsv,xslx. (subject to correction.)
- Logs and other things can be seen in PostgreSQL. Install PGAdmin and connect to the servers using the credentials used in the configurations/setup. Enable the firewall for your client machine.