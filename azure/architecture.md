# Core Architectural Components of Azure
WIth the help of Azure, you have everything you need to build your next great solution. 
## Azure Accounts
To create and use Azure services, you need an Azure subscription. After you've created an Azure account, you are free to create additional subscriptions. For example, a company might use a single Azure account for the business and create separate subscriptions for development, marketing, and sales departments. After creating a subscription you can create resources within them. 


### Azure free account
- free access to popular Azure products for 12 months
- a credit to use for the first 30 days
- access to more than 25 products that are always free

To sign up you need a phone number, credit card, and a Microsoft or GitHub account. The card is not charged unless you upgrade to a paid subscription

### Azure free student
- free access to certain Azure services for 12 months
- a credit to use in the first 12 months
- free access to certain software developer tools

## The Microsoft Learn Sandbox
a created temporary subscription that is added to your account to allow for the completion of learning modules. 

Allows for the use of:
- Powershell cli
- BASH cli
- Azure cli
    - interactive mode where it functions like an IDE
- Azure portal

## Azure physical infrastructure
The core architectural components of Azure

### Physical infrastructure
The infrastructure for Azure starts with datacenters. Conceptually, the datacenters are the same as large corporate datacenters. They are facilities with resources arranged racks, dedicated power, cooling and networking infrastructure

datacenters are grouped into Azure Regions or Azure Availability Zones. They are designed for resiliency and reliability.

### Region
A region is a geographical area on the planet that contains at least one, but potentially multiple datacenters that are nearby and networked together with low-latency. 

When you deploy a resource in Azure you typically have to select a region where you want it deployed. 

### Availability Zones
Availability zones are physically separated datacenters within an Azure region. Each availability zone is made up of one or more datacenters equipped with independent power, cooling, and networking. An availablity zone is set to be an isolation boundary. If one zone fails the others continue working. AZ's are connected through high-speed fiber-optic networks. 

You want to ensure your services and data are redundant so you can protect your information in case of failure. When you host your infrastructure, setting up your own redundancy requires that you create duplicate hardware environments. Azure can help make your app highly available through availability zones.

You can use availability zones to run mission-critical applications and build high-availability into your application architecture by co-locating your compute, storage, networking, and data resources within an availability zone and replicating in other availability zones. Keep in mind that there could be a cost to duplicating your services and transferring data between availability zones.

Availability zones are primarily for VMs, managed disks, load balancers, and SQL databases. Azure services that support availability zones fall into three categories:

- Zonal services: You pin the resource to a specific zone (for example, VMs, managed disks, IP addresses).
- Zone-redundant services: The platform replicates automatically across zones (for example, zone-redundant storage, SQL Database).
- Non-regional services: Services are always available from Azure geographies and are resilient to zone-wide outages as well as region-wide outages.

It is still possible to have all AZ's within a region fail, in which case further resiliance can be achieved through region pairs

### Region Pairs
Most Azure regions are paired with another region within the same geography (US, Europe, Asia) at least 300 miles away. This reduces the chance of interrupts due to things such as natural disasters, civil unrest, power outages. If an outage occurs the services automatically fail over to the other region pair. 

Ex. US-West paired with US-East, South East Asia paired with East Asia

Additional Advantges: 
- if an extensive outage occurs, one region out of every pair is prioritized to make sure one is restored as quickly as possible for applications hosted in that pair
- planned Azure updates are rolled out to pair regions one region at a time to minimize downtime and risk of outage
- data continues to reside within the same geography as its pair except Brazil South


### Sovereign Regions
Isolated from main instance of Azure. May be needed for compliance purposes

Regions include: 
- US DoD Central, US Gov Virginia, US Gov Iowa and more: These regions are physical and logical network-isolated instances of Azure for U.S. government agencies and partners. 
- China East, China North, and more, through partnership between 21Vianet where Microsoft doesn't directly maintain the datacenters. 



## Azure Management Infrastructure
The management infrastructure includes resources, resource groups, subscriptions, and accounts. 

### Azure resources and resource groups
a resource is a basic building block. Anything you create or provision is a resource. Virtual Machines, virtual networks, databases, cognitive services, etc are all resources. 

Resource gourps are simply groupings of resources. When you create a resource you are required to put it into a resource group. A resource group can have many resources but a resource can only have one resource group. 

Resource groups provide a convenient way to group resources together. When you apply an action to a resource group, that action will be applied to all resources in the resource group. If you delete a resource group all resources will be deleted.

Make a resource group structure that best fits your needs


## Azure Subscriptions
Subscriptions are a unit of management, billing and scale. 