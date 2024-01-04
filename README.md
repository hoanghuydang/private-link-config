# private-link-config

***LAB Precursor:***

It is important to highlight that during the initial deployment, all resources were exposed directly to the internet. 
Specifically, the Virtual Machines had their Network Security Groups and built-in firewalls configured in an open manner, allowing broad access. 
Additionally, other deployed resources were equipped with public endpoints that were visible to the internet, thereby eliminating the necessity for private endpoints in this setup.

In this lab, we will apply a Network Security Group to our subnet. 
We will enable Private Endpoint for our storage account and our Virtual Network as well, which takes them off the public internet and only makes them accessible within our Subnet and Virtual Networks.

***High-Level Overview:***

+ Inspect MDC Regulatory Compliance (Available and Implemented) NIST 800-53 (Ref) We will Implement SC-7
+ Configure Azure Private Link and Firewall for your Azure Key Vault instance
+ Ensure you use the same region and VNet the rest of your VMs are in
+ Configure Azure Private Link and Firewall for your Azure Storage Account instance
+ Disable Public Access (you can only access from within your VMs now.)
+ This is done on the network tab as well as the Settings -> configuration “Allow Blob public access → Disabled” as well
+ Observe Network Watcher Topology for the region and resource group all of your stuff is in.
+ Observe the Key Vault and Storage Account Private Endpoints are there
+ Login to “windows-vm” and check the IP addresses of your Key Vault and Storage Account instances.
+ They should be private addresses, indicating the resources have been probably integrated into private VNet:


***Step 1: Disable Public Access In Key Vaults & Allow trusted MS services to bypass this firewall***
![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/55f37d2a-272f-42e4-b47d-b496cddc9c9b)


***Step 2: Configure Private Endpoint***
![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/1e9c687b-021e-44e6-ab8b-4e9ac9221ee3)
![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/4d83b351-0c24-481e-8675-05c888fec9c3)
![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/a776d5fc-21d7-4d8e-9e1a-8214dc0a8cad)
![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/23fe9ea4-69bd-4023-8509-51b5a771a3ac)
![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/1b1dc935-8825-4880-96df-97954664a1a6)
![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/d0ad36c5-2692-4a67-b076-db1adf679267)


***Step 3: Disable Blob***
![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/541f2a40-cc37-4b36-a94b-9fa79651ca46)
![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/827b5fe6-1c26-44f0-8bda-accb21b461fe)

***Step 4: Configure Storage Account***
![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/97e630ff-740a-4f9d-971b-7ac8c51b69d3)
![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/0481a0b0-3ddb-458d-b857-a4a96354c8e4)
![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/4ddea5ec-8559-4656-bffc-cea4a0b7a51c)
![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/5771760e-4264-4f2e-bfed-77acae961f0f)
![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/b9d1b946-a896-43bf-ac70-7a9169e07c3d)
![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/4bd956a1-2f27-46d5-84e1-d459a6646a6b)

***Step 5: Observe Network Topology for the region and resource group all our entities are in***
![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/2c95b046-9fb4-49bc-98f3-4884a8c98c80)
![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/18a1b77e-3ead-4b93-823d-f9a0f14e873c)
![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/c38c5974-9cf8-4298-acb3-e68248afd4e4)
![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/897c9cc1-329d-4937-a05d-75744223806c)
![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/31f16816-acf0-4a55-973e-facc3dd72658)
![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/b34a948b-b188-4c22-9801-86ec176514ba)


Network topology refers to the structured layout of interconnected devices within a computer network. 
It encompasses the arrangement of servers, computers, and other components, along with the paths through which data flows. 
A well-designed network topology is crucial for security, as it can impact the ease or difficulty with which unauthorized access or attacks can occur. 
Secure network topology involves the strategic placement of security measures, such as firewalls and intrusion detection systems, to safeguard against potential threats and ensure the integrity of data transmissions.

***Step 6: Go to “windows-vm” and check the IP addresses of your Key Vault and Storage Account instances***
![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/d0a7626f-225e-4db5-b871-5eefc54f7bdf)
![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/d267645f-86ad-4c02-a889-40a04df3b6b8)

From my "windows-vm" - because it is in the Vnet

![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/fa89b761-517f-437d-bcc7-abd4f29e6b8b)

From my home MAC computer - Public IP Address

![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/886c0a5a-5229-4e1c-9f3f-b7734d40b771)

This confirms the key vault is set up with Private Endpoint correctly.

***Step 7: Check Storage Account***

Copy the Blob Service

![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/852d4ff8-a9a5-4811-9163-5440a643545b)

From my MAC:

![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/33e9aaf1-2704-4e04-a781-9e5340e9e363)

From my "windows-vm" - It is configured correctly Address is ***10.0.0.7***

![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/77ca7bf6-7807-4edc-9b31-1cb2b3e373d1)
![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/6646369a-3491-4636-9622-9c266a85ea83)

***Step 8: Create a Network Security Group and attach it to our Subnet***
Make sure it is in the correct Resource Group and Region
![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/f124c40c-8bae-4c55-8a9d-267097d5686d)
![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/92c19af6-ed45-4f36-a950-0122f8567752)

Viewing the Topology:

![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/086b37e9-9de0-4fe5-a573-99800cdbf870)
![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/8e523a71-8c07-4693-8ba4-5ee740e76e76)

***This confirms that we have connected our NSG to our Subnet***

![image](https://github.com/hoanghuydang/private-link-config/assets/127445164/d9cff5ea-26bd-4ab7-a74d-25a7326b681e)

***Lab Fin.***
