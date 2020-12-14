# Chatbot Resources

1. app-cpd-apps-arqna-<env>-we-01 - App service for Arabic QnA
2. app-cpd-apps-bot-<env>-we-01 - App service for Bot API
3. app-cpd-apps-qna-<env>-we-01 - App service for English QnA
4. 



# Chatbot Deployment Steps



## LUIS QnAMaker Deployments

1. Trigger [CD-BotLuisQnAInitialDeploy](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=542&_a=summary) Pipeline which will deploy 6 QnAMaker instances three for English and three for Arabic each for Source FAQ, Destination FAQ and KB, then four Luis instances two for English and two for Arabic each for General and Dispatch LUIS. 
It also generates a config json file in the build artifacts which will contain all the details of the LUIS and QnAMaker instances. 
This pipeline should be triggered only once on first deployment.

2. Copy the config json generated in step 1 and update it to the app configuration of the infra repo so that the bot when deployed uses this app configuration.

## BOT Api Deployment

1. Trigger [CD-Bot-Release-Master](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=293&_a=summary) which will trigger deployment of Bot Api, two Azure functions - QnAMakerSync and LuisTrainer Functions.

2. Configurations for these are in infra app settings.

## Bot WebChat Deployment

1. Trigger [CD-WebApps-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=130) which will deploy bot webchat into blob storage which will be available in cdn used in the marketplace, eservices portals and mobile app.

# Configuration Details for BOT

1. After triggering infra repo components, we have to update redirect url for the webapp bot appid Azure AD and also update microsoft as authentication account, so that bot api user name password login is allowed to access from bot client.
