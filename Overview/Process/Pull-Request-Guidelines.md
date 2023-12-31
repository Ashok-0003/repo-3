**API**

- No inline try catch blocks. Exception should be automatically bubble to exception handling middleware.
- Any changes in API like adding a new API or updating an existing one should reflect in swagger.json file located in the API project location.
- Any Sonar/Style cop suppression should be part of .editorconfig which is located at the root of the repo, however **avoid** any such suppressions.
- All magic numbers/strings should be declared as static integers/strings.
- All service changes should have relevant unit tests.
- Variables should have proper names. Names like obj, test should be avoided and should be descriptive. Similarly function names should be descriptive and follow naming guidelines, for example asynchronous methods should end with Async.
- Secrets should be part of keyvault and all the configuration changes should be updated for all the environments.
- KeyVault URL name should contain only alphanumeric name and dashes.

**Angular/JavaScript/TypeScript**
- Look for any possible missing null checks.
