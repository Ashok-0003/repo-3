
**B2B Portal**
| **ID** | **Dev Process** | **Tool** | **Responsible** | **Accountable** | **Consulted** | **Informed** |
|--|--|--|--|--|--|--|--|
| 1 | Change the status of User Story from 'Approved' to 'Committed' state and create child Tasks for development | ADO | Developer | Developer | Dev Lead | Dev Lead |
| 2 | Create a Feature branch for each work item and change the status of user story from 'Committed' to 'Under Development'| Visual Studio, Git, ADO | Developer | Developer | Dev Lead | Dev Lead |
| 3 | Develop code in Feature branch. Ensure compliance with SonarQube, JSLint, FXcop, StyleCop, CodeMetrics, FXcop Roslyn Analyser | Visual Studio, Git | Developer | Developer | Dev Lead | Dev Lead |
| 4 | Check-in code in Feature branch | Visual Studio, Git | Developer | Developer | Dev Lead | Dev Lead |
| 5 | Conduct unit test in Feature branch | Jasmine, NUnit, XUnit | Developer | Dev Lead | Dev Lead | Project Manager | 
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
| 1 | |  | | |  | |
| 2 | |  | | |  | |
| 3 | |  | | |  | |

**CMS** 
| **ID** | **Dev Process** | **Tool** | **Responsible** | **Accountable** | **Consulted** | **Informed** |
|--|--|--|--|--|--|--|--|
| 1 | |  | | |  | |
| 2 | |  | | |  | |
| 3 | |  | | |  | |

**API** 
| **ID** | **Dev Process** | **Tool** | **Responsible** | **Accountable** | **Consulted** | **Informed** |
|--|--|--|--|--|--|--|--|
| 1 | |  | | |  | |
| 2 | |  | | |  | |
| 3 | |  | | |  | |


**Chatbot** 
| ID | Dev Process | Tool | Responsible | Accountable | Consulted | Informed |
|--|--|--|--|--|--|--|--|
| 1 | Create a Feature branch for each work item | Visual Studio, Git, Bot framework emulator | Developer | Developer | Dev Lead | Dev Lead |
| 2 | Check-in code in Feature branch | Visual Studio, Git | Developer | Developer | Dev Lead | Dev Lead |
| 3 | Conduct unit test in Feature branch | Visual studio Unit test | Developer | Dev Lead | Dev Lead | Project Manager | 
| 4 | Submit Pull Request from Feature branch to merge code changes to master branch | Visual Studio, Git | Developer | Developer | Dev Lead | Dev Lead |
| 5 | Review the PR and approve for merging to master (or provide feedback for developer to address) | Visual Studio, Git | Dev Lead | Dev Lead | Architect | Developer |
| 6 | Delete Feature branch | Visual Studio, Git | Dev Lead | Dev Lead | Developer | Developer | 
| 7 | Create a build from master branch and deploy the solution in Dev environment | CI/CD pipelines | DevOps Engineer | Dev Lead | Dev Lead | Test Lead | 
| 8 | Validate code in Dev environment against acceptance criteria | Visual Studio, Git | Developer | Dev Lead | Dev Lead | Dev Lead | 
| 9 | Deploy code in TEST environment | CI/CD pipelines | DevOps Engineer | Dev Lead | Test Lead | Test Lead | 
| 10 | Validate code in TEST environment against acceptance criteria | ADO | Test Lead | Dev Lead | Dev Lead | Test Lead | 
| 11 | Publish release notes to Malomatia to deploy code in UAT | Email | DevOps Engineer | Dev Lead | Test Lead | Project Manager | 