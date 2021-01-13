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

# Webapp Bot AD update

1. After successful deployment of chatbot resources in step 1 above, we have to update manifest file and variable group with secret. for that follow below steps:

a. Go to the webapp bot resource created like below screenshot and select manage as highlighted in image below.
![image.png](/.attachments/image-9a7719e9-834a-4b31-9863-7cd60f72eb1e.png)
b.  Then click on manifest like below image and download the json file.
![image.png](/.attachments/image-330dfc10-197b-42a4-8ca1-481893222739.png)
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
select certificates and secrets and generate a secret and copy that to the variable group for all environments value: BotAppSecret
![image.png](/.attachments/image-bc0d6906-187c-4ac1-b088-fda9b1840486.png)

# Chatbot Deployment Steps



## LUIS QnAMaker Deployments

1. Trigger [CD-BotLuisQnAInitialDeploy](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=542&_a=summary) Pipeline which will deploy 6 QnAMaker instances three for English and three for Arabic each for Source FAQ, Destination FAQ and KB, then four Luis instances two for English and two for Arabic each for General and Dispatch LUIS. 
It also generates a config json file in the build artifacts which will contain all the details of the LUIS and QnAMaker instances.
**Detailed instructions available on updating config entries below :** [Update config entries by referring this](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&_a=edit&pagePath=%2FOverview%2FDevOps%2FChatbot%20Information%20and%20Deployment%20Steps&pageId=123&anchor=updating-infra-repo-with-luis-and-qna-keys) 
**This pipeline should be triggered only once on first deployment**.

2. Copy the config json generated in step 1 and update it to the app configuration of the infra repo so that the bot when deployed uses this app configuration. [Refer this](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&_a=edit&pagePath=%2FOverview%2FDevOps%2FChatbot%20Information%20and%20Deployment%20Steps&pageId=123&anchor=updating-infra-repo-with-luis-and-qna-keys).

3. Update the LUIS instances in this portal with Authoring resource if its empty. (https://eu.luis.ai/)
a. go to above url and then select directory and then choose authoring resource like image below.
 ![image.png](/.attachments/image-64fbb0ee-4266-40f7-98b2-d63d2b23c60f.png)
![image.png](/.attachments/image-9f073d5a-6a5d-48f2-999a-5d76cf94349e.png)
![image.png](/.attachments/image-b2ec52ae-43ba-4cd3-9f5b-5f377faedeeb.png)

b. you will see these language resources - two for english and two for arabic - each having instance for General and dispatch.

![image.png](/.attachments/image-7511e615-116c-4e8d-8550-f14b5933406b.png)

c. select each resource and follow steps below:
i. click on manage then azure resources and then add prediction resource
![image.png](/.attachments/image-10b330ad-e340-43fc-b935-913c1a40d20e.png)
ii. select cog-cpd-apps-luisrt-<env>-we-01 in the prediction resource.
![image.png](/.attachments/image-3cd24810-1e8e-47c2-9ccc-96055556e9cf.png)
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

![published.PNG](/.attachments/published-515af584-91c5-45a9-bff1-3a8a8647e669.PNG)

2. Download outputCognitiveModels.json file from that artifact as shown in the following image.

![outputcog.PNG](/.attachments/outputcog-95cca4eb-2872-49c1-818b-09a79d88d8d1.PNG)

3. The outputCognitiveModels.json file contains LUIS and QnA keys which now should be mapped to infra repo under _infra\Scripts\AppConfigurations\settings\\**<env>**\appsettings.json_ where **<env>** is the environment for which pipeline was executed.
4. Following are the keys from outputCognitiveModels.json whose values should be mapped to appsettings.json in infra.



| From (OutputCognitiveModels.json) | To infra\Scripts\AppConfigurations\settings\\**<env>**\appsettings.json  |
|--|--|
| Refer this - [Image](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&_a=edit&pagePath=%2FOverview%2FDevOps%2FChatbot%20Information%20and%20Deployment%20Steps&pageId=123&anchor=%22luiscustomendpoint%22) | "LuisCustomEndpoint" |
| Refer this - [Image](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&_a=edit&pagePath=%2FOverview%2FDevOps%2FChatbot%20Information%20and%20Deployment%20Steps&pageId=123&anchor=%22dispatchluisappiden%22) | "DispatchLuisAppIdEn" |
| "cognitiveModels" -> "en-us" -> "languageModels" -> "appid": | "GeneralLuisAppIdEn" |
| Refer this - [Image](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&_a=edit&pagePath=%2FOverview%2FDevOps%2FChatbot%20Information%20and%20Deployment%20Steps&pageId=123&anchor=%22dispatchluisappidar%22) | "DispatchLuisAppIdAr" |
| "cognitiveModels" -> "ar-ar" -> "languageModels" -> "appid": | "GeneralLuisAppIdAr" |
| "cognitiveModels" -> "en-us" -> "knowledgebases" -> "endpointKey": | "EnQnaMaker": { "EndpointKey" |
| Refer this - [Image](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&_a=edit&pagePath=%2FOverview%2FDevOps%2FChatbot%20Information%20and%20Deployment%20Steps&pageId=123&anchor=%22enqnamaker%22%3A-%7B-%22endpoint%22) | "EnQnaMaker": { "Endpoint" |
| "cognitiveModels" -> "en-us" -> "knowledgebases" -> "hostname" | "EnQnaMaker": { "Hostname" |
| "cognitiveModels" -> "en-us" -> "knowledgebases" -> "kbId" **where "id": "FAQ_en_us"** | "EnQnaMaker": { "FaqKbId" |
| "cognitiveModels" -> "en-us" -> "knowledgebases" -> "kbId" **where "id": "CRMKnowledgebase_en_us"** | "EnQnaMaker": { "KbQnAKbId" |
| "cognitiveModels" -> "en-us" -> "knowledgebases" -> "kbId" **where "id": "Source_FAQ_en_us"** | "EnQnaMaker": { "SourceFAQKbId" |
| "cognitiveModels" -> "ar-ar" -> "knowledgebases" -> "endpointKey": | "ArQnaMaker": { "EndpointKey" |
| Refer this - [Image](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&_a=edit&pagePath=%2FOverview%2FDevOps%2FChatbot%20Information%20and%20Deployment%20Steps&pageId=123&anchor=%22arqnamaker%22%3A-%7B-%22endpoint%22) | "ArQnaMaker": { "Endpoint" |
| "cognitiveModels" -> "ar-ar" -> "knowledgebases" -> "hostname" | "ArQnaMaker": { "Hostname" |
| "cognitiveModels" -> "ar-ar" -> "knowledgebases" -> "kbId" **where "id": "FAQ_ar_ar"** | "ArQnaMaker": { "FaqKbId" |
| "cognitiveModels" -> "ar-ar" -> "knowledgebases" -> "kbId" **where "id": "CRMKnowledgebase_ar_ar"** | "ArQnaMaker": { "KbQnAKbId" |
| "cognitiveModels" -> "ar-ar" -> "knowledgebases" -> "kbId" **where "id": "Source_FAQ_ar_ar"** | "ArQnaMaker": { "SourceFAQKbId" |

# Reference images:
- Follow [this](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&_a=edit&pagePath=%2FOverview%2FDevOps%2FChatbot%20Information%20and%20Deployment%20Steps&pageId=123&anchor=luis-qnamaker-deployments) to reach following pages in (https://eu.luis.ai/).
### "LuisCustomEndpoint" 
![luiscustom.PNG](/.attachments/luiscustom-51065cae-3af2-443d-aa18-5ce929cda728.PNG)

### "DispatchLuisAppIdEn"
![dispacthId.PNG](/.attachments/dispacthId-9355345c-6d30-4804-9c60-0dabebe93694.PNG)

### "DispatchLuisAppIdAr"
![dispatchar.PNG](/.attachments/dispatchar-13f01db8-5625-44a4-9cc7-8c2fb6dff3e9.PNG)

### "EnQnaMaker": { "Endpoint"
![endpoint-en.PNG](/.attachments/endpoint-en-0011cf21-d0a4-43a8-9336-413c4c30364b.PNG)

### "ArQnaMaker": { "Endpoint"
![endpoint-ar.PNG](/.attachments/endpoint-ar-e4f5a927-14e8-4f7e-bae2-2ee54b1dfd6a.PNG)

## Add/Update Keys in Azure DevOps Variable Groups
After updating infra repo, following Keys needs to be added/updated in the variable groups:

- **LuisGeneralAppIdEn** - From updated _infra\Scripts\AppConfigurations\settings\\**<env>**\appsettings.json_
- **LuisGeneralAppIdAr** - From updated _infra\Scripts\AppConfigurations\settings\\**<env>**\appsettings.json_
      - The above two Keys are used to update appId for English and Arabic LUIS General services under _**/platfom-apis/pipelines/bot/cognitiveModels.json**_
- **Bot-AppSettings-LuisAuthSubscriptionKey** 

![luis-auth-subs.PNG](/.attachments/luis-auth-subs-519a745d-fe61-4835-9f61-0c53351ea8c9.PNG)

- **Bot-AppSettings-LuisRtSubscriptionKey**

![luis-rt-subs.PNG](/.attachments/luis-rt-subs-f32698a6-1eae-4c27-9c0c-4693f85941d0.PNG)

- **Bot-AppSettings-QnaArSubscriptionKey** - From "cognitiveModels" -> "en-us" -> "knowledgebases" ->  "subscriptionKey" inside OutputCognitiveModels.json downloaded under this step - [Link](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&_a=edit&pagePath=%2FOverview%2FDevOps%2FChatbot%20Information%20and%20Deployment%20Steps&pageId=123&anchor=updating-infra-repo-with-luis-and-qna-keys)
- **Bot-AppSettings-QnaEnSubscriptionKey** -  From "cognitiveModels" -> "ar-ar" -> "knowledgebases" ->  "subscriptionKey" inside OutputCognitiveModels.json downloaded under this step - [Link](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&_a=edit&pagePath=%2FOverview%2FDevOps%2FChatbot%20Information%20and%20Deployment%20Steps&pageId=123&anchor=updating-infra-repo-with-luis-and-qna-keys)




