# AZ 900 Fundamentals

## Module 1 - Cloud Concepts

Why we use cloud?

Compute and Storage

### Cloud Concepts

- High availability : shared responsibility

- Scalability and Elasticity : cater to your needs

- Agility : we can do things very fast

- Fault tolerance 

- Disaster recovery : backup

### CapEx vs OpEx

- Capital Expenditures (CapEx) : Server cost, Storage cost, Network cost, Backup and Archive cost, Disaster costs, Datacenter infrastructure cost, Technical personnel

- Operational Expenditures (OpEx) : Leasing of software and features, Scaling charges based on usage, Billing at the user level

### Cloud Models

- Public Cloud : managed by a third party can be leased

- Private Cloud : on premise, owned by the company

- Hybrid Cloud : combines public and private cloud, most flexible model (do you want to do)

### Cloud Services

- Infrastructure as a Service (IaaS) : pay-as-you-go services such as storage, networking and virtualization

- Platform as a Service (PaaS) : hardware and software tools available over the internet

- Software as a Service (SaaS) : software that’s available via a third-party over the internet

    *On-premise - software that’s installed in the same building as your business

---

## Module 2 - Cloud Azure Services

### Geographies - discrete markets 

- Regions - collection of data centers
    *cost, location, services - factors on choosing a region

- Region Pairs - for fail over in case of disasters 
    *at least 300 miles separation

### For 2 or more VM

- Availability Zones : protection from entire datacenter failures

- Availability Sets : protecting against failure within datacenter

### Azure VM : IaaS

*Resource Group must be made first

- can be automated by JSON templates

- Bastion - safe and secure RDP alternative

### Azure App services : PaaS

### Azure Serverless Computing 

Containers 
- fast and efficient way to run an app
- run on common ground on regardless of its OS

### Azure Network Services

- Azure Virtual Network
- Azure Load Balancers
- VPN Gateway
- Azure Application Gateway
- Content Delivery Network
- VNet Peering

### How to connect on-prem to cloud?

- Point-to-site network connection (connect to vpn)

- Site-to-site network connection (must be public facing and is connected to azure)

    *100Mbps (by default speed)

### Data Categories

- Structured : SQL, …

- Semi-structured : JSON, HTML, …

- Unstructured : PDFs, JPGs, videos, …

### Storage Account

*name must be globally unique

- LRS : 3 copies of your data 

- GRS : 6 copies of your data (3 in region 3 on peer region)

### Azure Database Services

- Cosmos DB
- Azure SQL DB
- Database Migration

### Azure Marketplace

- Service on azure connects end user with solutions

### Microsoft IOT

- IOT Central : general IOT service for monitoring
- IOT Hub : bi-directional connection (monitor and control)

### Azure Synapse Analytics

- Data warehouse

### Azure HDInsight

### Azure Data Lake Analytics

- on demand analytics

### Azure Machine Learning

- Azure Machine Learning Service - for data scientist
- Azure Machine Learning Studio - for noobs

### Serverless Computing

- Azure Function - create based on events
- Azure Logic apps - create workflows make a decision 
- Azure Event grid - events routing service

### DevOps (old Visual Studio)

- for developers 

### Azure App Services

### Management Tools

*Learn to automate 

- Azure portal
- Poweshell
- CLI
- Cloud shell

---

## Module 3 - Security, Privacy, Compliance, and Trust

### Defense in Depth - layered approach security

- Shared security : based between provider and consumer 

- Authentication : establish identity

- Authorization : role based actions

### Azure Active Directory

- cloud based IAM service

- user and groups

- multi-factor authentication (something you know, something you possess, something you are)

### Securing the network

*Understand network security groups (NSG)

- Perimeter layer (Layer 7 Firewall, DDOS Protection)

- Network layer (Network Security Group)

### Network Watcher

- Effective security rules : statistics on rules

- Ip flow verifier : Ping

- Next Hop : Traceroute

### Security Center

- Detect, Assess, and Diagnose

### Key Vault

- place where to stores certificates and keys

### Azure Information Protection

- protect by labelings/classification 

### Advance Threat Protection

- understand your patterns and access if malicious actions are being done

### Governance

- Policies : way to govern users

- Initiatives : group of policies

### Resource Lock

- Read only : can’t modify resource group

- CanNotDelete : can’t delete resource group

### Azure Blueprints

- create reusable environments

### Subscription Governance

- Billing 

- Access Control 

- Subscription Limits 

### Tags

- provides metadata on Azure resources

### Azure Monitor

- collect, analyze, and act on Activity logs and Metrics

### Azure Service Health

- notify azure service issues

### Azure Advisor 

- recommendations on optimizations

### Azure Trust Center

- compliance

---

## Module 4 - Pricing and Support

### Azure Subscription

### Management Groups

### Pricing and Purchasing

Depends

- Enterprise

- Web Direct

Factors

- Resource type 

- Service

- Region
 
### Zones Price

- egress traffic

### Pricing Calculator

- estimate cost associated with your usage

*Location prices differ

*Understand how to save money

*Understand licenses

---

Online path

https://docs.microsoft.com/en-us/learn/paths/azure-fundamentals/

White paper

aka.ms/azfunpath