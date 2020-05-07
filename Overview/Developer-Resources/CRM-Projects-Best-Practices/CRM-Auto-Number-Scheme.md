# Overview

This document describes the Auto Number scheme used for each group of Entities in Dynamics.
These auto generated number will serve as an alternative key to the record GUID exposed by the platform, as an easy reference for the channels.

Each entity that is exposed through the API's will contain an additional field called "Alternate Key" that will be configured to the following schemes. **

##**Entities**

Prefix-[Seed]

Contact (Profile) : USR-[1000000000]
Account (Organisation) : ORG-[100000000]
Organisation Profile Link : OPL-[10000000000]
**Notification Templates**

Email Template : EML-[10000]
SMS Template : SMS-[10000]
Mobile Push Notification : MPN-[10000]

**Metadata/ Lookup Values**

Country : CMP-[10000]
Municipality : CPM-[20000]
Zone : CPM-[30000]
Taxonomy : CPM-[40000]
Taxonomy Items : CPM-[50000]

## **Excluded Entities**

The following entities will be excluded to as special considerations need to be taken into account.

Case (Complaints/Service Requests)
Default auto number functionality will be used.

**Product (Marketplace Catalogue)**

Will use use a different number convention that is still to be confirmed.
The proposed SKU number convention would need to cater for the following circumstances.

**Activity Entities (Email, SMS, Mobile Push)**
These are excluded to avoid any potential performance bottlenecks due to the volume of these records.


