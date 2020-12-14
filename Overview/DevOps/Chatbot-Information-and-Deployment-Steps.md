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



## LUIS QnAMaker Deployments

1. Trigger [CD-BotLuisQnAInitialDeploy](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=542&_a=summary) Pipeline which will deploy 6 QnAMaker instances three for English and three for Arabic each for Source FAQ, Destination FAQ and KB, then four Luis instances two for English and two for Arabic each for General and Dispatch LUIS. 
It also generates a config json file in the build artifacts which will contain all the details of the LUIS and QnAMaker instances. 
This pipeline should be triggered only once on first deployment.

2. Copy the config json generated in step 1 and update it to the app configuration of the infra repo so that the bot when deployed uses this app configuration.

3. Update the LUIS instances in this portal with Authoring resource. (https://eu.luis.ai/)

4. we can access QnAMaker instances in this url - https://www.qnamaker.ai/Home/MyServices

## BOT Api Deployment

1. Trigger [CD-Bot-Release-Master](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=293&_a=summary) which will trigger deployment of Bot Api, two Azure functions - QnAMakerSync and LuisTrainer Functions.

2. Configurations for these are in infra app settings.

## Bot WebChat Deployment

1. Trigger [CD-WebApps-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=130) which will deploy bot webchat into blob storage which will be available in cdn used in the marketplace, eservices portals and mobile app.

# Configuration Details for BOT

1. After triggering infra repo components, we have to update redirect url for the webapp bot appid Azure AD and also update microsoft as authentication account, so that bot api user name password login is allowed to access from bot client.
