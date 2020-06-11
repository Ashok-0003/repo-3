# An user story is considered "Done" when:

1. Code is checked-in in Azure DevOps, attached to a task and the build succeeds without any errors or warnings
1. Code has been peer-reviewed and lead reviewed (apply to Task completion)
1. Automated unit tests (for components containing business logic) are in place, follows the checklist guidance and offers >70% of code coverage for those components
1. Automated unit tests are successful (pass percentage is 100%, apply to Task completion)
1. Deployment script changes (if applicable) have been done in Azure DevOps
1. Static Code Analysis is run with results meeting the baselined quality gates 
1. Acceptance criteria are covered by successful tests
1. Integration Tests and Functional Tests have been created and passed
1. Functionality has been verified on DEV/QA environment (100% dev and test cycle pass percentages)