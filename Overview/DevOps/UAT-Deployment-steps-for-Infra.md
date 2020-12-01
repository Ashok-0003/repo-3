[TASMU Landing Zone BOM.xlsx](/.attachments/TASMU%20Landing%20Zone%20BOM-0a24bf9d-e274-40c8-addf-3a93c99166ff.xlsx)

As it is shown in the attached "Tasmu Landing Zone Bom.xlsx" file, UAT and other environments networks created based on pre-defined Vnets/Subnets and IP allocations.
IP allocations were checked with MOTC and Microsoft CSU team so that all the environment networks are properly defined and vnets/subnets are created. 

Also, as it is explained in the BOM file, UAT environment naming convention is defined for all resource groups and resources. It is expected from all developers to follow naming convention for any deployments.

Because of all development environments sits in the same development subscription, they can all use shared infra services like; Firewall, key vaults, storages etc.
