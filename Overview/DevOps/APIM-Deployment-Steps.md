**Pre-requisities**

1. API developed and deployed in an environment with AKS endpoint url.
2. Swagger.json file uploaded in the project folder of the API.
3. Policy.xml file for the api
4. Suffix name for the api to be used in APIM.

**Deployment of Azure Infrastructure**

Execute the resource group based CD pipeline, for example sandbox environment: [SBX Pipeline](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=254)

Estimated Time: 15mins

**Below are the Deployment of the APIM solution components:**

1. Update the Swagger.json file in the following path: './Input/apis/ProfileApi/1.0/' where ProfileApi is folder created in api name.
2. create a api policy xml file refer this file, can reuse it directly if any changes needed do that and place it in a folder(create if doesn't exist) under input/apis/ with the api name/1.0/ like this:
`/Input/apis/ProfileApi/1.0/apiServicePolicy.xml`
   Content of sample policy xml file:
`
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
3. Add the API details in the [valid.yml](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/apim-api-config?path=%2Fpipelines%2FAPIM%2Fsrc%2FInput%2Fvalid.yml&version=GBmain&_a=contents) file like below:
-    Under apis element in that api file add the below content and update it related to your api, like name, displayname, description, apiversion, apiversiondescription, api revision.
- Here the name field is used in all places in next steps (from below sample name is : **ProfileApi**)

    
```
- name: ProfileApi
      type: http
      displayName: Profile API
      description: Profile API
      serviceUrl:
      openApiSpec: './../../../src/services/Mcs.Tasmu.Profile.Api/Mcs.Tasmu.Profile.Api/Swagger.json'
      policy: './Input/apis/ProfileApi/1.0/apiServicePolicy.xml'
      suffix: profile
      subscriptionRequired: false
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
`openApiSpec: './Input/apis/ProfileApi/1.0/Swagger.json'`
-   Update policy value with apiServicePolicy.xml file path created as part of step 2.
`policy: './Input/apis/ProfileApi/1.0/apiServicePolicy.xml'`
- Update suffix value as per the [excel file](https://microsofteur.sharepoint.com/:x:/r/teams/TASMUNationalPlatform-DeliveryStream-MicrosoftOnly/_layouts/15/Doc.aspx?action=edit&sourcedoc=%7B402304D9-A074-41C8-A796-CDDC69CF0B6B%7D&cid=0283f482-f352-4a80-b6e6-26baadf70389).
`      suffix: profile`

3. Update the TemplateAndParameters/(environment-folder)/BackendUrlParameters.json [file](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/platform-apis?path=%2Fpipelines%2FAPIM%2Fsrc%2FInput%2FTemplateAndParameters%2Fdev%2FBackendUrlParameters.json) with the name of your api(name mentioned in step 2 - as per this sample its **ProfileApi**) as an key and value will be url of api(aks host name for that environment) in the environment with suffix as mentioned in the above step.
`{
        "apiName": "ProfileApi",
        "apiUrl": "http://172.20.42.30/profile"
 },`

4.  Update the [Pipeline.yml file](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/platform-apis?path=%2Fpipelines%2FAPIM%2FDeployment%2FPipeline%2FTemplates%2FtestandDeployTemplate.yml&version=GBmaster&_a=contents) with APIM instance name created in Azure infrastructure creation section along with resource group.

            
```
            sandbox:
              environment: sbx
              resourceGroupName: rg-cpd-apps-sbx-we-01
              apimName: apim-cpd-apps-sbx-we-01
            dev:
              environment: dev
              resourceGroupName: rg-cpd-apps-dev-we-01
              apimName: apim-cpd-apps-dev-we-01
            test:
              environment: tst
              resourceGroupName: rg-cpd-apps-tst-we-01
              apimName: apim-cpd-apps-tst-we-01
```




5. After this add the api related entry in CI pipeline(link provided in step 6) like below:

  
```
- template: templates/build-template.yml
    parameters:
      name: ProfileApi
      solutionFolder: "ProfileApi"
      componentStorageAccountSubscriptionIdParam: $(componentStorageAccountSubscriptionId)
      componentStorageAccountNameParam: $(componentStorageAccountName)
      componentStorageContainerNameParam: $(componentStorageContainerName)
      ServiceConnectionForAPIMParam: $(ServiceConnectionForAPIM)
```



6. After all the above 4 steps trigger the pipeline name: [CI-APIMConfig-Master-Build](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=570) CI-APIMConfig-Master-Build to generate the ARM templates. Configure the list of apis added newly/modified with semicolon separated values of the api names (as per this sample the name is **ProfileApi**) used in step 3 to the variable of the above pipeline value: `buildQueueInit`.By running this it will generate ARM templates for all the three environments for the apis passed in variables. Variable value look like below: - `ProfileApi;`


7. After this add the api related entry like below in CD pipelines for each environment files listed in step 8:

      
```
- template: ./Templates/testandDeployTemplate.yml
        parameters:
          FolderForApiVal: ProfileApi
          dependsonParam: previousapi
```

          

8. After this run the Release pipeline based on environment for the APIMConfiguration to be deployed.

- [CD-APIMConfig-sbx-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=571)
- [CD-APIMConfig-dev-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=572)
- [CD-APIMConfig-tst-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=573)
- [CD-APIMConfig-tra-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=574)
- [CD-APIMConfig-uat-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=575)

9. For executing each pipeline CI and CD pipelines you must pass your pipeline key(name given in step 3: for our example its `"ProfileApi"`) as variable of the pipeline so that only your api executes when running pipeline without wasting resources by executing all apis.


10. Refer [this PR](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/platform-apis/pullrequest/1222) where we have added two apis newly


**Estimated Time:**
1. For Updating the contents in above section steps and swagger file uploading: 20Mins
1. For Running CI pipeline for an API: 40 Mins
1. For Running CD pipeline for an API in an environment: 2 Mins

