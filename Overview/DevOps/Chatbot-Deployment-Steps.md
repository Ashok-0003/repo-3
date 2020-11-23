# Chatbot Deployment Steps

1. Trigger [CD-BotLuisQnAInitialDeploy](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=542&_a=summary) Pipeline which will deploy four QnAMaker instances two for English and two for Arabic each for FAQ and KB, then four Luis instances two for English and two for Arabic each for General and Dispatch LUIS. 
It also generates a config json file in the build artifacts which will contain all the details of the LUIS and QnAMaker instances. 
This pipeline should be triggered only once on first deployment.

2. Copy the config json generated in step 1 and update it to the app configuration of the infra repo so that the bot when deployed uses this app configuration.

3. 