# User Setup

- Set owner of the workflows of TASMU Processes solution to a service account (ex. svc.crm.pre@tasmusqcpprod.onmicrosoft.com).
- Then change the aforementioned user's Business unit to "**SQCP**" BU. The Owner of work flow should have "**System Administrator**" role. Make sure the security role is assigned again after changing BU (because roles gets removed while changing BU).
- Then update the “SensitiveRecordsOwnerId” id value in the system configuration to the build user's user id. For Build User, Business unit should be in "**TASMU**" and it should also have "**System Administrator**" role.