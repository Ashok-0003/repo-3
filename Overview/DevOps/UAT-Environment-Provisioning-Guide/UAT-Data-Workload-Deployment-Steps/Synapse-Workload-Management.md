# Synapse Workload Management

Physical server isolation can lead to pockets of infrastructure that are underutilized, overbooked or in a state where caches are constantly being primed with hardware starting and stopping. A successful workload management scheme effectively manages resources, ensures highly efficient resource utilization, and maximizes return on investment (ROI).

A data warehouse workload refers to all operations that transpire in relation to a data warehouse. The depth and breadth of these components depend on the maturity level of the data warehouse. The data warehouse workload encompasses:

- The entire process of loading data into the warehouse
- Performing data warehouse analysis and reporting
- Managing data in the data warehouse
-  Exporting data from the data warehouse.


The performance capacity of a data warehouse is determined by the data warehouse units.

- To view the resources allocated for all the performance profiles, see Memory and concurrency limits.
- To adjust capacity, you can scale up or down.

## Workload management concepts
Dedicated SQL pool workload management in Azure Synapse consists of three high-level concepts:
- Workload Classification
- Workload Importance
- Workload Isolation

### Workload Classification
Workload classification is the concept of assigning a request to a workload group and setting importance levels. Historically, this assignment was done via role membership using sp_addrolemember. This action can now be done via the CREATE WORKLOAD CLASSIFER. The classification capability provides a richer set of options such as label, session, and time to classify requests.[Full description of Workload Classification is available here.](https://docs.microsoft.com/en-us/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-workload-classification)

### Workload Importance
Workload importance influences the order in which a request gets access to resources. On a busy system, a request with higher importance has first access to resources. Importance can also ensure ordered access to locks.
[Full description of Workload Importance is available here.](https://docs.microsoft.com/en-us/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-workload-isolation)

### Workload Isolation
Workload isolation reserves resources for a workload group. Resources reserved in a workload group are held exclusively for that workload group to ensure execution. Workload groups also allow you to define the amount of resources that are assigned per request, much like resource classes do. Workload groups give you the ability to reserve or cap the amount of resources a set of requests can consume. Finally, workload groups are a mechanism to apply rules, such as query timeout, to requests.
[Full description of Workload Isolation is available here.](https://docs.microsoft.com/en-us/azure/synapse-analytics/sql-data-warehouse/sql-data-warehouse-workload-importance)