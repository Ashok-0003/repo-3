For development tenant environments:
1. Create a private DNS Zone – privatelink.westeurope.azmk8s.io
1. Add Vnet linking to hub network:
	vnet-cph-pltf-prd-we-01
1. Deploy the clusters in CPD subscription
1. [To deploy the private cluster in a vNET with a custom DNS and private DNS Zone](https://docs.microsoft.com/en-us/azure/aks/private-clusters#configure-private-dns-zone) 
   We are using a preview feature - AKS Preview version 0.5.7 or later
1. Once the clusters has been created and configured, unlink the private DNS zone from CPH Vnet
1. In CPH, create a private DNS Zone – privatelink.westeurope.azmk8s.io
1. Add Vnet linking to hub network:
	vnet-cph-pltf-prd-we-01
1. Move the DNS A records from CPD private DNS Zone to CPH private DNS zone
1. The above step is required due to multi-tenant hub spoke model and till the support for SPNs/managed identities is added across tenants.
1. Test the connectivity to clusters.
1. Detailed documentation on cluster configuration will be shared separately.

Production environments:
1. Cluster will be created by providing the resource Id of private DNS Zone in CPH.
2. [To deploy the private cluster in a vNET with a custom DNS and private DNS Zone](https://docs.microsoft.com/en-us/azure/aks/private-clusters#configure-private-dns-zone) 
	We are using a preview feature - AKS Preview version 0.5.7 or later


