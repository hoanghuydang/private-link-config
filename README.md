# private-link-config

***LAB Precursor:***

It is important to highlight that during the initial deployment, all resources were exposed directly to the internet. 
Specifically, the Virtual Machines had their Network Security Groups and built-in firewalls configured in an open manner, allowing broad access. 
Additionally, other deployed resources were equipped with public endpoints that were visible to the internet, thereby eliminating the necessity for private endpoints in this setup.

In this lab, we will apply a Network Security Group to our subnet. 
We will enable Private Endpoint for our storage account and our Virtual Network as well, which takes them off the public internet and only makes them accessible within our Subnet and Virtual Networks.

***High-Level Overview:***

Inspect MDC Regulatory Compliance (Available and Implemented)
NIST 800-53 (Ref)
We will Implement SC-7

Configure Azure Private Link and Firewall for your Azure Key Vault instance
Ensure you use the same region and VNet the rest of your VMs are in

Configure Azure Private Link and Firewall for your Azure Storage Account instance
Disable Public Access (you can only access from within your VMs now.)
This is done on the network tab as well as the Settings -> configuration “Allow Blob public access → Disabled” as well

Observe Network Watcher Topology for the region and resource group all of your stuff is in.
Observe the Key Vault and Storage Account Private Endpoints are there

Login to “windows-vm” and check the IP addresses of your Key Vault and Storage Account instances.
They should be private addresses, indicating the resources have been probably integrated into private VNet:

Possible causes for this are your resources and VM are actually in different Virtual Networks, or something is just not setup right

The good news is, you don’t need to fix this for the rest of the lab, we are just trying to lock down the environment. However, if you want to fix it, you can try deleting the Private Endpoints/config and trying again

***Step 1:*** Disable Public Access In Key Vaults
![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/55f37d2a-272f-42e4-b47d-b496cddc9c9b)
