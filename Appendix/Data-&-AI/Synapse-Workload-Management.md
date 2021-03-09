Azure Synapse Workload Management is a solution which allows the operator to manage the workload regarding the needs.


| Metric name | Description | Aggregation Type  |
|--|--|--|
| Effective cap resource percent |Effective cap resource percent is a hard limit on the percentage of resources accessible by the workload group, taking into account Effective min resource percentage allocated for other workload groups. The Effective cap resource percent metric is configured using the CAP_PERCENTAGE_RESOURCE parameter in the CREATE WORKLOAD GROUP syntax. The effective value is described here. For example if a workload group DataLoads is created with CAP_PERCENTAGE_RESOURCE = 100 and another workload group is created with an Effective min resource percentage of 25%, the Effective cap resource percent for the DataLoads workload group is 75%. The Effective cap resource percent determines the upper bound of concurrency (and thus potential throughput) a workload group can achieve. If additional throughput is needed beyond what is currently reported by the Effective cap resource percent metric, either increase the CAP_PERCENTAGE_RESOURCE, decrease the MIN_PERCENTAGE_RESOURCE of other workload groups or scale up the instance to add more resources. Decreasing the REQUEST_MIN_RESOURCE_GRANT_PERCENT can increase concurrency, but may not increase overall throughput.  |  |
|  |  |  |
|  |  |  |
|  |  |  |
|  |  |  |

