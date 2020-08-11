**Below are the APIM Deployment Steps:**

1. Update the Swagger.json file in the API source folder of that api.
2. Add the API details in the [valid.yml](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/platform-apis?path=%2Fpipelines%2FAPIM%2Fsrc%2FInput%2Fvalid.yml&version=GBmaster&_a=contents) file like below:
     a. Under apis element in that api file add the below content and update it related to your api, like name, displayname, description, apiversion, apiversiondescription, api revision

    
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
