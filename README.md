# Cloud Landscape for Application Project

This repository contains  an Azure Resource Manager (ARM) template designed to construct a cloud architecture tailored for application projects. The ARM template facilitates the creation of the following infrastructure:

![infrastructure](https://github.com/bakr-mostafa/cloud-landscape-app-project/blob/main/infrastructure.png)


## Specifications

### Resource Group (RG1)
- Contains all resources deployed for the application project.

### Virtual Network (VNet1)
- Subnet1
- VM-jumper-01: A VM that acts as a jumper to access the web server VMs using RDP. The VM-jumper-01 is accessed only via Azure Bastion.

### Virtual Network (VNet2)
- BackSub: Subnet containing the web server VMs. Can access storage using Service Endpoint only.
- AzureFirewallSubnet: Subnet containing the Azure Firewall associated with VNet2.
- GatewaySubnet: Subnet used to connect with Windows Admin Center (WAC).
- VM-web-01, VM-web-02: Web server VMs hosting Internet Information Services (IIS) web servers.
- Load Balancer: Distributes inbound traffic from the internet after being filtered by Azure Firewall. Ensures business continuity by distributing traffic among the two web servers.
- Azure Firewall: Filters traffic coming from the internet, forwards it to the load balancer, and restricts access to web servers to specific domains.

### Storage and File Share
- Utilizes Azure Storage for file storage needs.
- Implements a file share accessible by the web server VMs in the BackSub subnet for efficient file sharing and collaboration. Access to the file share is restricted to the BackSub subnet using Service Endpoint.
  
### On-Premises Infrastructure
- Utilizes Hyper-V for on-premises virtualization.
- Integrates on-premises infrastructure seamlessly with Azure cloud services for centralized management and streamlined operations using Windows Admin Center (WAC).




