# User Setup

- Set owner of the workflows in TASMU Processes solution to a valid service account (ex. svc.crm.pre@tasmusqcpprod.onmicrosoft.com) other than the build user.
  - Make sure the aforementioned user's Business unit is "**SQCP**" BU.
  - The Owner of work flow should have "**System Administrator**" role.
  - Make sure the security role is assigned again after changing BU (because roles gets removed while changing BU).
- Then update the “SensitiveRecordsOwnerId” id value in the system configuration to the build user's user id.
  - For build user, business unit should be in "**TASMU**" and it should also have "**System Administrator**" role.
  - This system configuration must be updated in ADO pipeline's [configuration file](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/crm-platform?path=%2Fpipelines%2Fbuild%2Fconfig).
  - As of this writing, build user is named "spn-crm-*env-service-connection" in each environment.
- Update/verify the business unit of application users used by APIs.
  - These users should be in SQCP BU. **Make sure the security role is assigned again after changing BU (because roles gets removed while changing BU).**
    - Profile Management
    - Case Management
    - Common Integration
    - Profile Daemon