# Development Environment

# Test Environment:
## Node Size
Standard_DS3_v2
## Auto-Scaling
Cluster Auto-scaling TURNED ON; Node count: 2(min) – 6(max)  
Horizontal Pod Auto-scaling TURNED ON: min Pod count of 2
Minimum default POD count should be 3 for all except CMS API
CMS API PODs: Auto-scale or fixed count of 8
