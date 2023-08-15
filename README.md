# Synapse Hub and Spoke Deployment

This repository outlines the provisioning of Synapse Hub Workspace with centralized Azure Data Lake storage to be shared by all Synapse Spoke Workspaces. This can also be extended to Dedicated SQL Pool, Spark Pool, and Data Explorer Pool if required. These 3 components are out of scope for this exercise.

* [Create a private link hub](https://learn.microsoft.com/en-us/azure/synapse-analytics/security/synapse-private-link-hubs)
* [How to connect to hub workspace via private link](https://learn.microsoft.com/en-us/azure/synapse-analytics/security/how-to-connect-to-workspace-with-private-links)

### Steps to follow -

1) Create a private link hub
2) Add service tags for 4 services for pass thru
3) Create Hub Virtual Network
4) Create Synapse hub workspace with private Hierarchical Azure Data Lake Storage
5) Create 2 spoke Synapse workspaces with private Hierarchical Azure Data Lake Storage
6) Create 2 Virtual Networks in respective spokes
7) Peer both spoke Virtual Network with hub Virtual Network
8) Create private endpoints in 2 spoke workspaces
9) Add a managed identity for storage blob contributor and storage contributor to hub workspace for both spoke workspaces
10) Connect private endpoint to a hub resource for Hierarchical Azure Data Lake Storage
11) The method in #9 is an alternative to the hub/spoke Virtual Network peering
12) Create a link Sercive in spokes to connect to storage in the hub via managed identity

### Future needs 
* Create a link service in spokes to connect to other resources in the hub workspace e.g.: SQL pool, spark pool, ADX pool, etc.
* Create a private link for the aforementioned resources

### Hub Architecture
![Image](https://github.com/avidunixuser/synapsehubandspoke/blob/main/Architecture/hubandspoke.jpg)

### Deploy Private Link Hub to Azure

[![Deploy To Azure](https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/1-CONTRIBUTION-GUIDE/images/deploytoazure.svg?sanitize=true)](https://github.com/avidunixuser/synapsehubandspoke/blob/main/SynapseHub/template.json)

### Spoke 1 Architecture

<img src="https://github.com/avidunixuser/synapsehubandspoke/blob/main/Architecture/synapsespoke1.jpg" width="400" />

### Deploy Synapse Spoke1 to Azure

[![Deploy To Azure](https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/1-CONTRIBUTION-GUIDE/images/deploytoazure.svg?sanitize=true)](https://github.com/avidunixuser/synapsehubandspoke/blob/main/SynapseSpoke1/template.json)

### Spoke 2 Architecture

<img src="https://github.com/avidunixuser/synapsehubandspoke/blob/main/Architecture/synapsespoke2.jpg" width="400" />

### Deploy Synapse Spoke2 to Azure

[![Deploy To Azure](https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/1-CONTRIBUTION-GUIDE/images/deploytoazure.svg?sanitize=true)](https://github.com/avidunixuser/synapsehubandspoke/blob/main/SynapseSpoke2/template.json)

> [!IMPORTANT]
> To minimize cost related to this sample it is recommended to delete the resources groups for Hub and both the spokes when it is not needed.


