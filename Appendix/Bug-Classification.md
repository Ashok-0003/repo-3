# Category Definitions

|Value| Description |
|--|--|
| Not a Defect | The logged bug in not a valid bug and needs to be rejected. E.g. understanding gap, incorrect behavior expected, no such requirement outlined per user story. There is not action required from the development bug on such bugs. |
|Third-Party integration  | Bugs raising due to integration components owned by different vendors. E.g. 6D payment related bug where both MS and 6D might be required to investigate and resolution. |
| Duplicate bug | Any incorrect system behavior logged as bug, but there is another bug outlining the same issue. Such bugs will be marked as “Removed” and linked to the original bug (decided based on which is logged earlier in the ADO). |
| Functional | Indicate the bug is gap in requirements outlined as per user story (or FR if applicable) and the corresponding implementation in the TASMU platform. The behavior must be explicit per the user story to classify the bug as valid bug. Any implicit requirement unless clearly discussed during elaboration meetings needs to be logged as an observation or enhancement request for the platform. |
| Non-Functional | <p>Categorization of NFR related bugs into appropriate category for better tracking and resolution. MS will accept bugs related to the testing scope.</p><p>**NOTE:** Any bug not in-scope of MS testing needs to be discussed in triaged and prioritized, based on criticality and impact for the successful go-live of the TASMU platform. Such bugs can be prioritized by respective workstream PjMs depending on the available capacity and needs to be re-tested by OC testing team.</p>|

# Root Cause Definitions
|Value| Description |
|--|--|
|Architectural / Design Issue| Bugs resulting from issues / understanding gap in the current architecture or designing of the platform|
|Chatty interface leading to too many  remote calls|Bugs resulting due to multiple calls or payload that can be optimized by the development team|
|Code not optimized|Bugs resulting due to non-adherence to coding guidelines or best practices|
|Coding/Deployment/Build/Config Issues|Bugs resulting from incorrect coding logic, missing deployment, incorrect build artifacts or config issues|
|Dependency not met||
|Deployment/Build issue||
|DoD was not met||
|DoR was not met||
|Implicit requirement||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||