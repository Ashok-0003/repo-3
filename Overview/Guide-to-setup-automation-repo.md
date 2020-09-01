#### **PRE-REQ**: UPDATE `<packageSources>` & `<packageSourceCredentials>` IN **`%appdata%/Nuget/Nuget.config`** 
```xml
<!-- Update %appdata%/Nuget/Nuget.config -->
<configuration>
  <packageSources>
    <add key="nuget.org" value="https://api.nuget.org/v3/index.json" protocolVersion="3" />
    <add key="CD-Bdd.Core" value="https://vsogd.pkgs.visualstudio.com/_packaging/CD-Bdd.Core/nuget/v3/index.json" />
  </packageSources>
  ...
  <packageSourceCredentials>
    <!-- Update Credentials -->
    <CD-Bdd.Core>
      <add key="Username" value="user@microsoft.com" />
      <add key="ClearTextPassword" value="VstsPersonalAccessToken" />
    </CD-Bdd.Core>
  </packageSourceCredentials>
</configuration>

```  
> Replace `user@microsoft.com` above with your email
> Replace `VstsPersonalAccessToken` above with your [PAT](https://vsogd.visualstudio.com/_usersSettings/tokens)

Steps to clone the BDD Automation code:
1.	Automation code URL: ‘https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/automation?path=%2Fsrc’
2.	Clone the repo locally using the above url.
 
9. Make sure that the Package sources for Bdd.Core are available as below:
 ![image.png](/.attachments/image-02bb7ec0-fe15-441f-b28a-713d63253608.png)

11.	Also make sure that the Package Restore option is enabled as shown below:
 ![image.png](/.attachments/image-c16f79a0-b97d-4e17-b3a0-64eb8e04b56d.png)
12.	Once the changes are applied, one should able to build the solution and execute the tests.

**Automation Repo Layout**

This Automation repo accounts for both API and web automation project (we might have mobile automation project included to the same repo in future). And this repo is shared across domains, so currently BizApps, MA and MW are using the same repo for tracking automation.

Below is layout of the repo:
![image.png](/.attachments/image-bbd1ccc4-e897-47f2-8d07-46cd3e5886be.png)
One can find tests related to ModernApps under PlatformServices folder.

Note: Since we are using the Bdd framework for automation, one will be finding the test steps written in gherkins under "Features" folder and the corresponding implementation in "StepDefinitions"