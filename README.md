# Synapse Hub and Spoke Deployment

This repository outlines the provisioning of Synapse Hub Workspace with centralized Azure Data Lake storage to be shared by all Synapse Spoke Workspaces. This can also be extended to Dedicated SQL Pool, Spark Pool, and Data Explorer Pool if required. These 3 components are out of scope for this exercise.

> [!IMPORTANT]
> The following documentation was referred to create this repository

* [Create a private link hub](https://learn.microsoft.com/en-us/azure/synapse-analytics/security/synapse-private-link-hubs)
* [How to connect to hub workspace via private link](https://learn.microsoft.com/en-us/azure/synapse-analytics/security/how-to-connect-to-workspace-with-private-links)

### Steps to follow -

* Create a private link hub
* Add service tags for 4 services for pass thru
* Create Hub Virtual Network
* Create Synapse hub workspace with private Hierarchical Azure Data Lake Storage
* Create 2 spoke Synapse workspaces with private Hierarchical Azure Data Lake Storage
* Create 2 Virtual Networks in respective spokes
* Peer both spoke Virtual Network with hub Virtual Network
* Create private endpoints in 2 spoke workspaces
* Add a managed identity for storage blob contributor and storage contributor to hub workspace for both spoke workspaces
* Connect private endpoint to a hub resource for Hierarchical Azure Data Lake Storage
* The method in #9 is an alternative to the hub/spoke Virtual Network peering
* Create a link Sercive in spokes to connect to storage in the hub via managed identity

### Future needs 
* Create a link service in spokes to connect to other resources in the hub workspace e.g.: SQL pool, Spark Pool, ADX Pool, etc.
* Create a private link for the resources as mentioned above

### Hub Architecture
![Image](https://github.com/avidunixuser/synapsehubandspoke/blob/main/Architecture/hubandspoke.jpg)

### Deploy Private Link Hub to Azure

[![Deploy To Azure](https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/1-CONTRIBUTION-GUIDE/images/deploytoazure.svg?sanitize=true)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Favidunixuser%2Fsynapsehubandspoke%2Fmain%2FSynapseHub%2Ftemplate.json)

### Spoke 1 Architecture

<img src="https://github.com/avidunixuser/synapsehubandspoke/blob/main/Architecture/synapsespoke1.jpg" width="400" />

### Deploy Synapse Spoke1 to Azure

[![Deploy To Azure](https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/1-CONTRIBUTION-GUIDE/images/deploytoazure.svg?sanitize=true)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Favidunixuser%2Fsynapsehubandspoke%2Fmain%2FSynapseSpoke1%2Ftemplate.json)

### Spoke 2 Architecture

<img src="https://github.com/avidunixuser/synapsehubandspoke/blob/main/Architecture/synapsespoke2.jpg" width="400" />

### Deploy Synapse Spoke2 to Azure

[![Deploy To Azure](https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/1-CONTRIBUTION-GUIDE/images/deploytoazure.svg?sanitize=true)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Favidunixuser%2Fsynapsehubandspoke%2Fmain%2FSynapseSpoke2%2Ftemplate.json)

> [!IMPORTANT]
> To minimize cost related to this sample it is recommended to delete the resources groups for Hub and both the spokes when it is not needed.


