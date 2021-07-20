[[_TOC_]]
# Chatbot Resources

1. app-cpd-apps-arqna-<env>-we-01 - App service for Arabic QnA
2. app-cpd-apps-bot-<env>-we-01 - App service for Bot API
3. app-cpd-apps-qna-<env>-we-01 - App service for English QnA
4. cog-cpd-apps-luisauth-<env>-we-01 - Cognitive services LUIS Authoring
5. cog-cpd-apps-luisrt-<env>-we-01 - Cognitive Services LUIS Runtime
6. cog-cpd-apps-arqna-<env>-we-01 - Cognitive Services QnAMaker Arabic
7. cog-cpd-apps-qna-<env>-we-01 - Cognitive Services QnAMaker English
8. func-cpd-apps-luistra-<env>-we-01 - Function app Luis Trainer
9. func-cpd-apps-qnasync-<env>-we-01 - Function App QnAMaker Sync triggered by logic app for Knowledgebase data synchronize from CRM dynamics to QnAMaker and qnamaker copying from one qnamaker source instance to destination instance.
10. logic-cpd-apps-qnacopy-<env>-we-01 - Logic App QnAMaker FAQ copier from source to destination qnamaker specified in qnamaker section.
11. logic-cpd-apps-qnakbsync-<env>-we-01 - Logic App QnAMaker Knowledge articles Synchronizer from CRM dynamics to QnAMaker instance.
12. srch-cpd-apps-arcog-<env>-we-01 - Search Service Arabic Cognitive service for QnAMaker
13. srch-cpd-apps-cog-<env>-we-01 - Search Service English Cognitive Service for QnAMaker
14. bot-cpd-apps-<env>-we-01 - Webapp Bot

# LUIS (Language Understanding Intelligent Service)

1. tasmubot_ar_ar_Dispatch - Arabic Dispatch LUIS
2. tasmubot_ar_ar_General - Arabic General LUIS
3. tasmubot_en_us_Dispatch - English Dispatch LUIS
4. tasmubot_en_us_General - English General LUIS

# QnAMaker Instances

1. tasmubot_FAQ_ar_ar - Arabic FAQ Destination instance used in BOT
2. tasmubot_CRMKnowledgebase_ar_ar - Arabic Knowledgebase Instance synched from dynamics(CRM) used in BOT
3. tasmubot_Source_FAQ_ar_ar - Source FAQ instance used by Admin or User to create or update FAQ data.
4. tasmubot_FAQ_en_us - English FAQ Destination intance used in BOT
5. tasmubot_CRMKnowledgebase_en_us - English Knowledgebase Insatance synched from dynamics(CRM) used in BOT
6. tasmubot_Source_FAQ_en_us - Source FAQ instance used by Admin or User to create or update FAQ data.

# Chatbot Deployment Steps

## Items to be updated before triggering below CD-BotLuisQnAInitialDeploy pipeline

Below items to be updated in variable group refer the [screenshot reference](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/123/Chatbot-Information-and-Deployment-Steps?anchor=add%2Fupdate-keys-in-azure-devops-variable-groups) to know how to get these keys from azure portal:
1. Bot-AppSettings-LuisAuthSubscriptionKey
2. Bot-AppSettings-QnaEnSubscriptionKey
3. Bot-AppSettings-QnaArSubscriptionKey

NOTE: Above variables are also used for key-vault secret update for use inside bot Api also.

# Add Keys in Azure DevOps Variable Groups for CD-BotLuisQnAInitialDeploy pipeline
Before starting CD-BotLuisQnAInitialDeploy pipeline, following Keys needs to be added/updated in the variable groups:

- **Bot-AppSettings-LuisAuthSubscriptionKey** 

![luis-auth-subs.PNG](/.attachments/luis-auth-subs-69380917-ff77-4503-b2a3-ae7b69364649.PNG)

- **Bot-AppSettings-QnaArSubscriptionKey** 

![qna-ar-subs.PNG](/.attachments/qna-ar-subs-b474c2b0-259c-436c-9251-9d67871b3a03.PNG)

- **Bot-AppSettings-QnaEnSubscriptionKey** 

![qna-en-subs.PNG](/.attachments/qna-en-subs-1bce95d8-e43f-442f-a38c-d9b0241395cf.PNG)


## LUIS QnAMaker Deployments

1. Trigger [CD-BotLuisQnAInitialDeploy](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=542&_a=summary) Pipeline which will deploy 6 QnAMaker instances three for English and three for Arabic each for Source FAQ, Destination FAQ and KB, then four Luis instances two for English and two for Arabic each for General and Dispatch LUIS. 
It also generates a config json file in the build artifacts which will contain all the details of the LUIS and QnAMaker instances (Almost 90% of bot related configuration values will be available in this json file).
**Detailed instructions available on updating config entries below :** [Update config entries by referring this](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&_a=edit&pagePath=%2FOverview%2FDevOps%2FChatbot%20Information%20and%20Deployment%20Steps&pageId=123&anchor=updating-infra-repo-with-luis-and-qna-keys) 
**This pipeline should be triggered only once on first deployment**.

2. Copy the config json generated in step 1 and update it to the app configuration of the infra repo so that the bot when deployed uses this app configuration. [Refer this](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&_a=edit&pagePath=%2FOverview%2FDevOps%2FChatbot%20Information%20and%20Deployment%20Steps&pageId=123&anchor=updating-infra-repo-with-luis-and-qna-keys).

3. Update the LUIS instances in this portal with Authoring resource if its empty. (https://eu.luis.ai/)
a. go to above url and then select directory and then choose authoring resource like image below.

![luis.PNG](/.attachments/luis-0ec72fc2-4561-4976-bd79-8c28a008bac7.PNG)
![authoring-resource.PNG](/.attachments/authoring-resource-7885d0b9-e853-435b-9c0a-2533260e69a6.PNG)
![done-auth.PNG](/.attachments/done-auth-676eece2-a396-4c72-8fb9-c6c4a5a8bac9.PNG)

b. you will see these language resources - two for english and two for arabic - each having instance for General and dispatch.

![luis.PNG](/.attachments/luis-33dcb8da-8274-4af7-ad73-68cf934c9d42.PNG)

c. select each resource and follow steps below:
i. click on manage then azure resources and then add prediction resource

![prediction-resource.PNG](/.attachments/prediction-resource-b0631ecb-11cb-4e00-b6d9-bde2dba44fff.PNG)

ii. select cog-cpd-apps-luisrt-<env>-we-01 in the prediction resource.

![select-prediction.PNG](/.attachments/select-prediction-60ad7dab-0de4-4c09-a5dc-26888a247411.PNG)

iii. then hit this url once: 
https://func-cpd-apps-luistra-<env>-we-01.azurewebsites.net/api/locale/ar
https://func-cpd-apps-luistra-<env>-we-01.azurewebsites.net/api/locale/en


4. we can access QnAMaker instances in this url - https://www.qnamaker.ai/Home/MyServices

## BOT Api Deployment

1. Trigger [CD-Bot-Release-Master](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=293&_a=summary) which will trigger deployment of Bot Api, two Azure functions - QnAMakerSync and LuisTrainer Functions.

2. Configurations for these are in infra app settings.

## Bot WebChat Deployment

1. Trigger [CD-WebApps-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=130) which will deploy bot webchat into blob storage which will be available in cdn used in the marketplace, eservices portals and mobile app. [Bot webchat components available here](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/web-apps?path=%2Fbotwebchat%2Fbotwebchat).


# Updating Infra repo with LUIS and QNA keys
1. Once [CD-BotLuisQnAInitialDeploy](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build/resultsbuildId=22348&view=results) is successfully ran, it will publish single [artifact](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build/results?buildId=22348&view=artifacts&pathAsName=false&type=publishedArtifacts) specific to selected environment.

![published.PNG](/.attachments/published-1da4dee6-2822-4946-953d-f60787ed2af8.PNG)

2. Download outputCognitiveModels.json file from that artifact as shown in the following image.

![outputcog.PNG](/.attachments/outputcog-5a6ccd48-a177-46d3-ae52-8a18c9ecbae9.PNG)

3. The outputCognitiveModels.json file contains LUIS and QnA keys which now should be mapped to infra repo under _infra\Scripts\AppConfigurations\settings\\**<env>**\appsettings.json_ where **<env>** is the environment for which pipeline was executed.
4. Following are the keys from outputCognitiveModels.json whose values should be mapped to appsettings.json in infra.



| From (OutputCognitiveModels.json) | To infra\Scripts\AppConfigurations\settings\\**<env>**\appsettings.json  |
|--|--|
| Refer this - [Image](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&_a=edit&pagePath=%2FOverview%2FDevOps%2FChatbot%20Information%20and%20Deployment%20Steps&pageId=123&anchor=%22luiscustomendpoint%22) | "Bot.AppSettings:LuisCustomEndpoint" |
| Refer this - [Image](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&_a=edit&pagePath=%2FOverview%2FDevOps%2FChatbot%20Information%20and%20Deployment%20Steps&pageId=123&anchor=%22dispatchluisappiden%22) | "Bot.AppSettings:DispatchLuisAppIdEn" |
| "cognitiveModels" -> "en-us" -> "languageModels" -> "appid": | "Bot.AppSettings:GeneralLuisAppIdEn" |
| Refer this - [Image](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&_a=edit&pagePath=%2FOverview%2FDevOps%2FChatbot%20Information%20and%20Deployment%20Steps&pageId=123&anchor=%22dispatchluisappidar%22) | "Bot.AppSettings:DispatchLuisAppIdAr" |
| "cognitiveModels" -> "ar-ar" -> "languageModels" -> "appid": | "Bot.AppSettings:GeneralLuisAppIdAr" |
| "cognitiveModels" -> "en-us" -> "knowledgebases" -> "endpointKey": | "Bot.AppSettings:EnQnaMaker:EndpointKey" |
| Refer this - [Image](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&_a=edit&pagePath=%2FOverview%2FDevOps%2FChatbot%20Information%20and%20Deployment%20Steps&pageId=123&anchor=%22enqnamaker%22%3A-%7B-%22endpoint%22) | "Bot.AppSettings:EnQnaMaker:Endpoint" |
| "cognitiveModels" -> "en-us" -> "knowledgebases" -> "hostname" | "Bot.AppSettings:EnQnaMaker:Hostname" |
| "cognitiveModels" -> "en-us" -> "knowledgebases" -> "kbId" **where "id": "FAQ_en_us"** | "Bot.AppSettings:EnQnaMaker:FaqKbId" |
| "cognitiveModels" -> "en-us" -> "knowledgebases" -> "kbId" **where "id": "CRMKnowledgebase_en_us"** | "Bot.AppSettings:EnQnaMaker:KbQnAKbId" |
| "cognitiveModels" -> "en-us" -> "knowledgebases" -> "kbId" **where "id": "Source_FAQ_en_us"** | "Bot.AppSettings:EnQnaMaker:SourceFAQKbId" |
| "cognitiveModels" -> "ar-ar" -> "knowledgebases" -> "endpointKey": | "Bot.AppSettings:ArQnaMaker:EndpointKey" |
| Refer this - [Image](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&_a=edit&pagePath=%2FOverview%2FDevOps%2FChatbot%20Information%20and%20Deployment%20Steps&pageId=123&anchor=%22arqnamaker%22%3A-%7B-%22endpoint%22) | "Bot.AppSettings:ArQnaMaker:Endpoint" |
| "cognitiveModels" -> "ar-ar" -> "knowledgebases" -> "hostname" | "Bot.AppSettings:ArQnaMaker:Hostname" |
| "cognitiveModels" -> "ar-ar" -> "knowledgebases" -> "kbId" **where "id": "FAQ_ar_ar"** | "Bot.AppSettings:ArQnaMaker:FaqKbId" |
| "cognitiveModels" -> "ar-ar" -> "knowledgebases" -> "kbId" **where "id": "CRMKnowledgebase_ar_ar"** | "Bot.AppSettings:ArQnaMaker:KbQnAKbId" |
| "cognitiveModels" -> "ar-ar" -> "knowledgebases" -> "kbId" **where "id": "Source_FAQ_ar_ar"** | "Bot.AppSettings:ArQnaMaker:SourceFAQKbId" |

5. We need to also update following key in infra\Scripts\AppConfigurations\settings\<env>\appsettings.json

| KeyName | How to retrieve | Remarks |
|--|--|--|
| MicrosoftAppId | Go to bot-cpd-apps-<env>-we-01 and under settings tab, copy the Microsoft App Id | ![ms-bot-appid.PNG](/.attachments/ms-bot-appid-caf4af84-b4e2-4160-87e4-9a5b9c8d4ec8.PNG) |

# Reference images:
- Follow [this](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&_a=edit&pagePath=%2FOverview%2FDevOps%2FChatbot%20Information%20and%20Deployment%20Steps&pageId=123&anchor=luis-qnamaker-deployments) to reach following pages in (https://eu.luis.ai/).
### "LuisCustomEndpoint" 
![luiscustom.PNG](/.attachments/luiscustom-4b0fe2d5-87f0-4153-969a-646c7c1a5023.PNG)

### "DispatchLuisAppIdEn"
![dispacthId.PNG](/.attachments/dispacthId-35855c44-eb4e-4ff4-9ef2-4d0539f9a3d9.PNG)

### "DispatchLuisAppIdAr"
![dispatchar.PNG](/.attachments/dispatchar-9186252e-1f3b-440f-9ec0-5b8ce932f016.PNG)

### "EnQnaMaker": { "Endpoint"
![endpoint-en.PNG](/.attachments/endpoint-en-19684c2c-484d-42e1-a15e-0a8ea53e4fda.PNG)

### "ArQnaMaker": { "Endpoint"
![endpoint-ar.PNG](/.attachments/endpoint-ar-fe63e04c-6392-4c69-89c0-ec8e08bca714.PNG)

## Add Keys in Azure DevOps Variable Groups
After updating infra repo, following Keys needs to be added/updated in the variable groups:

- **LuisGeneralAppIdEn** - From updated _infra\Scripts\AppConfigurations\settings\\**<env>**\appsettings.json_
- **LuisGeneralAppIdAr** - From updated _infra\Scripts\AppConfigurations\settings\\**<env>**\appsettings.json_
      - The above two Keys are used to update appId for English and Arabic LUIS General services under _**/platfom-apis/pipelines/bot/cognitiveModels.json**_

- **Bot-AppSettings-LuisRtSubscriptionKey**

![luis-rt-subs.PNG](/.attachments/luis-rt-subs-a33610f0-e7e7-4bf0-8848-8d9daf590f08.PNG)


# Webapp Bot AD update

1. After successful deployment of chatbot resources as part of following Infra Deployment - [Link](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/119/UAT-Apps-Workload-Deployment-Steps), we have to update manifest file and variable group with secret. for that follow below steps:

a. Go to the webapp bot resource created like below screenshot and select manage as highlighted in image below.

![webappbot-manage.png](/.attachments/webappbot-manage-b419b3a8-ff19-4df3-8cce-3660542115c1.png)

b.  Then click on manifest like below image and download the json file.
![Manifest.png](/.attachments/Manifest-e06082d9-b90e-4b40-8cca-0e5bba332e90.png)

c. Then update following elements in the json with values below and upload it here.

```
"accessTokenAcceptedVersion": 2
"replyUrlsWithType": [	
		{	
			"url": "https://token.botframework.com/.auth/web/redirect",	
			"type": "Web"	
		}	
	],
"signInAudience": "AzureADandPersonalMicrosoftAccount",
```

d. Updating the Secret : 
Select certificates and secrets and generate new client secret with any meaningful description. Once generated copy that secret to **BotAppSecret** Key of the variable group which is present under AzureDevops->Pipelines->Library for all the environments.

![client-secret.png](/.attachments/client-secret-09a00977-1665-475d-851e-fd7082233e77.png)


## Bot DirectLine Setup in APIM

1. After the deployment of bot-cpd-apps-<env>-we-01 WebAppBot Azure resource, go to bot-cpd-apps-<env>-we-01 in Azure portal and perform the following steps.
a. Under Channels section, select Edit from Direct Line.

![bot-directline-1.PNG](/.attachments/bot-directline-1-05a5ba39-a9a8-42ab-a70d-c944f2dedaa7.PNG)

b. Copy the first secret and place it to the **Bot-Directline-Key** under variable groups of Azure Devops Pipeline specific to the environment - [Refer](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/219/Variable-Groups-Pipeline-Usage).
c. Enable these checkboxes **3.0** and **Block attachment upload from user**.
d. Enable **Enhanced authentication options**.
e. Click on **Add a trusted origin** and paste `https://api.<env>.sqcp.qa`.

###For more information
The above setup is used at following places:
1. DirectLine Swagger Page - [Link](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/apim-api-config?path=%2Fpipelines%2FAPIM%2Fsrc%2FInput%2Fapis%2FBotDirectlineApi%2FSwagger.json)
2. **Bot-Directline-Key** from the variable group is used in following pipeline - [Link](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/apim-api-config?path=%2Fpipelines%2FAPIM%2Fsrc%2FPipeline%2Ftemplates%2Fbuild-template.yml)


#Troubleshooting BOT Api in App service

##Troubleshoot - 500 Error on accessing Messages endpoint - Option 1

The error on accessing /api/messages endpoint if we get error like below picture then follow these steps:
![image.png](/.attachments/image-db4538e4-31c9-4622-afe1-89eb3145e239.png)

1. Go to App service where bot api is hosted and restart it.
2. Go to log stream then see the logs if it shows error like below image.
3. Then check whether the adaptive card is properly updated in app config store (acst-cpd-apps-str-<env>-we-01).

![image.png](/.attachments/image-ad787dc0-8cf5-42b1-9d78-47bde091178e.png)

4. Some of the adaptive card properties are below:
`"FindInformationMenuCard": "<base64 string>",
        "MainMenuCard": "<base64 string>",
        "RequestServiceOrSupportMenuCard": "<base64 string>"
     `
same above list is available for Arabic and English.
5. All the above fields should contain valid json adaptive card.

##Troubleshoot - 500 Error on accessing Messages endpoint - Option 2

The error on accessing /api/messages endpoint if we get error like below picture then follow these steps:
![image.png](/.attachments/image-db4538e4-31c9-4622-afe1-89eb3145e239.png)

1. Go to App service where bot api is hosted and restart it.
2. go to Kudu under Adavnced tools and click on Debug console and CMD.
3. then go to the following path C:\home\site\wwwroot>
4. then hit the following command as shown in below image 
`dotnet .\Mcs.TASMU.Bot.dll`
2. Then see the logs if it shows error like below image.
![image.png](/.attachments/image-773dc46c-0345-4ecc-9aa8-ea6ce5455a7b.png)
3. Then check whether the adaptive card is properly updated in app config store (acst-cpd-apps-str-<env>-we-01).


4. Some of the adaptive card properties are below:
`"FindInformationMenuCard": "<base64 string>",
        "MainMenuCard": "<base64 string>",
        "RequestServiceOrSupportMenuCard": "<base64 string>"
     `
same above list is available for Arabic and English.
5. All the above fields should contain valid json adaptive card.



#How to Update LUIS Dispatch Threshold score in BOT Api

Go to Platform-apis repo to this file [MainDialog](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/platform-apis?path=%2Fsrc%2Fservices%2FBOT%2FMcs.Tasmu.Bot%2FDialogs%2FMainDialog.cs&version=GBmaster&_a=contents)

At line 869 - change value 0.02 to the decided value and update in 885 line.
Refer screen shot below:
![image.png](/.attachments/image-e6e1846d-9626-4249-8644-519147f12727.png)


#How to Update QnaMaker Threshold score in BOT Api

Go to Platform-apis repo to this file [QnaMakerOptions](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/platform-apis?path=%2Fsrc%2Fservices%2FBOT%2FMcs.Tasmu.Bot.Models%2FQnAMakerOptions.cs&version=GBmaster&_a=contents)

At line 22 - change value 0.6f to the decided value.
Refer screen shot below:
![image.png](/.attachments/image-eeb82f4a-13fa-4582-afe1-cfee25ce4aa4.png)