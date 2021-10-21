
**B2B Portal, Chatbot, API**
| **ID** | **Dev Process** | **Tool** | **Responsible** | **Accountable** | **Consulted** | **Informed** |
|--|--|--|--|--|--|--|--|
| 1 | Change the status of User Story from 'Approved' to 'Committed' state and create child Tasks for development | ADO | Developer | Developer | Dev Lead | Dev Lead |
| 2 | Create a Feature branch for each work item and change the status of user story from 'Committed' to 'Under Development'| Visual Studio, Git, ADO | Developer | Developer | Dev Lead | Dev Lead |
| 3 | Develop code in Feature branch. Ensure compliance with SonarQube, JSLint, FXcop, StyleCop, CodeMetrics, FXcop Roslyn Analyser | Visual Studio, Git, Bot Framework Emulator (for Chatbot) | Developer | Developer | Dev Lead | Dev Lead |
| 4 | Check-in code in Feature branch | Visual Studio, Git | Developer | Developer | Dev Lead | Dev Lead |
| 5 | Conduct unit test in Feature branch - Angular (Jasmine), C# (XUnit), Chatbot (XUnit) | Jasmine, XUnit | Developer | Dev Lead | Dev Lead | Project Manager | 
| 6 | Submit Pull Request from Feature branch to merge code changes to master branch | Visual Studio, Git | Developer | Developer | Dev Lead | Dev Lead |
| 7 | Review the PR and approve for merging to master (or provide feedback for developer to address). Ensure compliance with SonarQube, JSLint, FXcop, StyleCop, CodeMetrics, FXcop Roslyn Analyser | Visual Studio, Git, SonarQube, JSLint, FXcop, StyleCop, CodeMetrics, FXcop Roslyn Analyser | Dev Lead | Dev Lead | Architect | Developer |
| 8 | Delete Feature branch | Visual Studio, Git | Dev Lead | Dev Lead | Developer | Developer | 
| 9 | Create a build from master branch and deploy the solution in Dev environment | CI/CD pipelines | DevOps Engineer | Dev Lead | Dev Lead | Test Lead | 
| 10 | Validate code in Dev environment against acceptance criteria (using test scripts from the test team) and update the status of user story from 'Under Development' to 'Dev Complete' | Visual Studio, Git, ADO | Developer | Dev Lead | Dev Lead | Dev Lead | 
| 11 | Deploy code in TEST environment | CI/CD pipelines | DevOps Engineer | Dev Lead | Test Lead | Test Lead | 
| 12 | Validate code in TEST environment against acceptance criteria and update the status of user story from 'Dev Complete' to 'Test Complete' | ADO | Test Lead | Dev Lead | Dev Lead | Test Lead | 
| 13 | Publish release notes to Malomatia to deploy code in UAT and change the status of user story from 'Test Complete' to 'DoD Ready' | Email | DevOps Engineer | Dev Lead | Test Lead | Project Manager | 

**CRM** 
| **ID** | **Dev Process** | **Tool** | **Responsible** | **Accountable** | **Consulted** | **Informed** |
|--|--|--|--|--|--|--|--|
| 1 | Change the status of User Story from 'Approved' to 'Committed' state and create child Tasks for development | ADO | Developer | Developer | Dev Lead | Dev Lead |
| 2 | If code change is involved, create a Feature branch for the work item. If only configuration is involved, then make the changes in Dev CRM environment first. And change the status of user story from 'Committed' to 'Under Development'| Visual Studio, Git, ADO, D365 | Developer | Developer | Dev Lead | Dev Lead |
| 3 | Develop code in Feature branch (if code involved) or make configuration changes in Dev CRM environment. Ensure compliance with SonarQube, JSLint, FXcop, StyleCop, CodeMetrics, FXcop Roslyn Analyser | Visual Studio, Git, D365 | Developer | Developer | Dev Lead | Dev Lead |
| 4 | Check-in code in Feature branch (if code involved) | Visual Studio, Git, D365 | Developer | Developer | Dev Lead | Dev Lead |
| 5 | Conduct unit test in Feature branch - C# (XUnit), manual unit testing of UI changes | XUnit, Microsoft Fakes | Developer | Dev Lead | Dev Lead | Project Manager | 
| 6 | Submit Pull Request from Feature branch to merge code changes to master branch (if code involved) | Visual Studio, Git | Developer | Developer | Dev Lead | Dev Lead |
| 7 | Review the PR and approve for merging to master if code involved (or provide feedback for developer to address). Ensure compliance with SonarQube, JSLint, FXcop, StyleCop, CodeMetrics, FXcop Roslyn Analyser | Visual Studio, Git, SonarQube, JSLint, FXcop, StyleCop, CodeMetrics, FXcop Roslyn Analyser | Dev Lead | Dev Lead | Architect | Developer |
| 8 | For configuration changes, review the changes in Dev CRM environment. After review, update the configuration in Config CRM environment. | D365 | Dev Lead | Dev Lead | Architect | Developer |
| 10 | Ensure compliance with solution checker tool | D365 [solution checker](https://docs.microsoft.com/en-us/powerapps/maker/data-platform/use-powerapps-checker) | Dev Lead | Dev Lead | Developer | Developer | 
| 9 | Delete Feature branch | Visual Studio, Git | Dev Lead | Dev Lead | Developer | Developer | 
| 10 | Create a build from master branch and deploy the solution in Dev environment | CI/CD pipelines | DevOps Engineer | Dev Lead | Dev Lead | Test Lead | 
| 11 | Validate code in Dev environment against acceptance criteria (using test scripts from the test team) and update the status of user story from 'Under Development' to 'Dev Complete' | Visual Studio, Git, ADO | Developer | Dev Lead | Dev Lead | Dev Lead | 
| 12 | Deploy code in TEST environment | CI/CD pipelines | DevOps Engineer | Dev Lead | Test Lead | Test Lead | 
| 13 | Validate code in TEST environment against acceptance criteria and update the status of user story from 'Dev Complete' to 'Test Complete' | ADO | Test Lead | Dev Lead | Dev Lead | Test Lead | 
| 14 | Publish release notes to Malomatia to deploy code in UAT and change the status of user story from 'Test Complete' to 'DoD Ready' | Email | DevOps Engineer | Dev Lead | Test Lead | Project Manager | 

**CMS** 
| **ID** | **Dev Process** | **Tool** | **Responsible** | **Accountable** | **Consulted** | **Informed** |
|--|--|--|--|--|--|--|--|
| 1 | Change the status of User Story from 'Approved' to 'Committed' state and create child Tasks for development.  | ADO | Developer | Developer | Dev Lead | Dev Lead |
| 2 | Create a Feature branch for each work item and change the status of user story from 'Committed' to 'Under Development'. Script and SPFx Changes (Infra Repo), CMS API and Functions(Platform Core and Platform API) | Visual Studio, Git, ADO, O365, PowerShell | Developer | Developer | Dev Lead | Dev Lead |
| 3 | Develop code in Feature branch. Ensure compliance with SonarQube, JSLint, FXcop, StyleCop, CodeMetrics, FXcop Roslyn Analyser | Visual Studio, Git, O365 | Developer | Developer | Dev Lead | Dev Lead |
| 4 | Check-in code in Feature branch | Visual Studio, Git | Developer | Developer | Dev Lead | Dev Lead |
| 5 | Conduct unit test in Feature branch - SPFx(Jest), C# (XUnit) | Jest, XUnit | Developer | Dev Lead | Dev Lead | Project Manager | 
| 6 | Submit Pull Request from Feature branch to merge code changes to master branch | Visual Studio, Git | Developer | Developer | Dev Lead | Dev Lead |
| 7 | Review the PR and approve for merging to master (or provide feedback for developer to address). Ensure compliance with SonarQube, JSLint, FXcop, StyleCop, CodeMetrics, FXcop Roslyn Analyser | Visual Studio, Git, SonarQube, JSLint, FXcop, StyleCop, CodeMetrics, FXcop Roslyn Analyser | Dev Lead | Dev Lead | Architect | Developer |
| 8 | Delete Feature branch | Visual Studio, Git | Dev Lead | Dev Lead | Developer | Developer | 
| 9 | Create a build from master branch and deploy the solution in Dev environment | CI/CD pipelines | DevOps Engineer | Dev Lead | Dev Lead | Test Lead | 
| 10 | Validate code in Dev environment against acceptance criteria (using test scripts from the test team) and update the status of user story from 'Under Development' to 'Dev Complete' | Visual Studio, Git, ADO | Developer | Dev Lead | Dev Lead | Dev Lead | 
| 11 | Deploy code in TEST environment | CI/CD pipelines | DevOps Engineer | Dev Lead | Test Lead | Test Lead | 
| 12 | Validate code in TEST environment against acceptance criteria and update the status of user story from 'Dev Complete' to 'Test Complete' | ADO | Test Lead | Dev Lead | Dev Lead | Test Lead | 
| 13 | Publish release notes to Malomatia to deploy code in UAT and change the status of user story from 'Test Complete' to 'DoD Ready' | Email | DevOps Engineer | Dev Lead | Test Lead | Project Manager | 

**DevOps - Infra**
| **ID** | **Dev Process** | **Tool** | **Responsible** | **Accountable** | **Consulted** | **Informed** |
|--|--|--|--|--|--|--|--|
| 1 | Create a Feature branch for each work item | Visual Studio, Git | DevOps Engineer | DevOps Engineer | DevOps Engineer | DevOps Engineer |
| 2 | Check-in code in Feature branch | Visual Studio, Git | DevOps Engineer | DevOps Engineer | DevOps Engineer | Architect |
| 3 | Conduct unit test in Feature branch | Azure Portal, Powershell | DevOps Engineer | DevOps Engineer | DevOps Engineer | Project Manager | 
| 4 | Submit Pull Request from Feature branch to merge code changes to master branch | Visual Studio, Git | DevOps Engineer | DevOps Engineer | DevOps Engineer | Architect |
| 5 | Review the PR and approve for merging to master (or provide feedback for developer to address) | Visual Studio, Git | DevOps Engineer | DevOps Engineer | Architect | Architect |
| 6 | Delete Feature branch | Visual Studio, Git | DevOps Engineer | DevOps Engineer | DevOps Engineer | DevOps Engineer | 
| 7 | Create a build from master branch and deploy the solution in Dev environment | CI/CD pipelines | DevOps Engineer | DevOps Engineer | DevOps Engineer | Test Lead | 
| 8 | Validate code in Dev environment against acceptance criteria | Visual Studio, Git | DevOps Engineer | DevOps Engineer | DevOps Engineer | Dev Lead | 
| 9 | Deploy code in TEST environment | CI/CD pipelines | DevOps Engineer | DevOps Engineer | Test Lead | Test Lead | 
| 10 | Validate code in TEST environment against acceptance criteria | ADO | Test Lead | DevOps Engineer | DevOps Engineer | Test Lead | 
| 11 | Publish release notes to Malomatia to deploy code in UAT | Email | DevOps Engineer | DevOps Engineer | Test Lead | Project Manager | 
