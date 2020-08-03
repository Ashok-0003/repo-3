**API**

- No inline try catch blocks. Exception should be automatically bubble to exception handling middleware.
- Any changes in API like adding a new API or updating an existing one should reflect in swagger.json file located in the API project location.
- Any Sonar/Style cop suppression should be part of .editorconfig which is located at the root of the repo.
- All magic numbers/strings should be declared as static integers/strings.
