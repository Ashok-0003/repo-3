**Below are the APIM Deployment Steps:**

1. Update the Swagger.json file in the API source folder of that api.
2. create a api policy xml file refer this file, can reuse it directly if any changes needed do that and place it in a folder(create if doesn't exist) under input/apis/ with the api name/1.0/ like this:
`/Input/apis/ProfileApi/1.0/apiServicePolicy.xml`
   Content of sample policy xml file:
`<!--
    IMPORTANT:
    - Policy elements can appear only within the <inbound>, <outbound>, <backend> section elements.
    - To apply a policy to the incoming request (before it is forwarded to the backend service), place a corresponding policy element within the <inbound> section element.
    - To apply a policy to the outgoing response (before it is sent back to the caller), place a corresponding policy element within the <outbound> section element.
    - To add a policy, place the cursor at the desired insertion point and select a policy from the sidebar.
    - To remove a policy, delete the corresponding policy statement from the policy document.
    - Position the <base> element within a section element to inherit all policies from the corresponding section element in the enclosing scope.
    - Remove the <base> element to prevent inheriting policies from the corresponding section element in the enclosing scope.
    - Policies are applied in the order of their appearance, from the top down.
    - Comments within policy elements are not supported and may disappear. Place your comments between policy elements or at a higher level scope.
-->
<policies>
    <inbound>
        <base />
    </inbound>
    <backend>
        <base />
    </backend>
    <outbound>
        <base />
    </outbound>
    <on-error>
        <base />
    </on-error>
</policies>`
3. Add the API details in the [valid.yml](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/platform-apis?path=%2Fpipelines%2FAPIM%2Fsrc%2FInput%2Fvalid.yml&version=GBmaster&_a=contents) file like below:
-    Under apis element in that api file add the below content and update it related to your api, like name, displayname, description, apiversion, apiversiondescription, api revision.

    
```
- name: ProfileApi
      type: http
      displayName: Profile API
      description: Profile API
      serviceUrl:
      openApiSpec: './../../../src/services/Mcs.Tasmu.Profile.Api/Mcs.Tasmu.Profile.Api/Swagger.json'
      policy: './Input/apis/ProfileApi/1.0/apiServicePolicy.xml'
      suffix: profile
      subscriptionRequired: true
      isCurrent: true
      apiVersion:
      apiVersionDescription: Profile Api first version
      apiVersionSetId:
      apiRevision: 1
      apiRevisionDescription: Profile Api first revision
      products: central-platform-core
      tags: TASMUAPIM, central-platform-core
      diagnostic:
        name: applicationinsights
        alwaysLog: allErrors
        loggerId: AppInsightsWillbeUpdatedinParameter
        sampling:
          samplingType: fixed
          percentage: 50
        frontend:
          request:
            headers:
            body:
              bytes: 512
          response:
            headers:
            body:
              bytes: 512
        backend:
          request:
            headers:
            body:
              bytes: 512
          response:
            headers:
            body:
              bytes: 512
        enableHttpCorrelationHeaders: true
```

-  Update openApiSpec value with Swagger.json file path created as per step 1.
`openApiSpec: './../../../src/services/Mcs.Tasmu.Profile.Api/Mcs.Tasmu.Profile.Api/Swagger.json'`
-   Update policy value with apiServicePolicy.xml file path created as part of step 2.
`policy: './Input/apis/ProfileApi/1.0/apiServicePolicy.xml'`
- Update suffix value as per the [excel file](https://microsofteur.sharepoint.com/:x:/r/teams/TASMUNationalPlatform-DeliveryStream-MicrosoftOnly/_layouts/15/Doc.aspx?action=edit&sourcedoc=%7B402304D9-A074-41C8-A796-CDDC69CF0B6B%7D&cid=0283f482-f352-4a80-b6e6-26baadf70389).
`      suffix: profile`

3. Update the TemplateAndParameters/(environment-folder)/BackendUrlParameters.json [file](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/platform-apis?path=%2Fpipelines%2FAPIM%2Fsrc%2FInput%2FTemplateAndParameters%2Fdev%2FBackendUrlParameters.json) with the name of your api as an key and value will be url of api(aks host name for that environment) in the environment with suffix as mentioned in the above step.
`{
        "apiName": "Profile",
        "apiUrl": "http://172.20.42.30/profile"
 },`

4.  