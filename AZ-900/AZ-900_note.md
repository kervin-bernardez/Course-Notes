# AZ 900 Microsoft Fundamentals

## Describe Cloud Concepts (15-20%) 

### Cloud Concepts

- High Availability = service accessibility

- Scalability = allows to increase or decrease resources horizontally(UP) or vertically (DOWN)

- Elasticity = allows to increase and decrease resources IN or OUT

- Agility = ability to rapid deploy

- Fault Tolerance = ability to operate while experiencing failure

- Disaster Recovery = ability to recover from large scale disruptions

### CapEx vs OpEx

- CapEx = tangible resources

- OpEx = intangible resources

- Economies of Scale = do things more efficiently at lower cost at large scale

- Consumption-based Model = pay-as-you-go

### Cloud Services

- IaaS = manages VM and OS (Ubuntu, CentOS, ...)

- PaaS = manages a service (Pfsense, OpenVPN, ...) without worrying about the VM and OS

- SaaS = manage only the software (GSuites, Office 365, ...)

### Cloud Models

- Public cloud = third-party managed cloud for lease (Azure, AWS, GCP)

- Private cloud = privately managed cloud resources (Nextcloud, OwnCloud, ...)

- Hybrid cloud = combination of public and private cloud

## Describe Core Azure Services (30-35%)

### Core Azure architectural components

- Regions = location of data centers

- Region Pairs = 300 miles apart data center paired for disaster recovery

- Availability Zones = protection from entire data center failure for fault tolerance

- Availability Sets = protection from rack failure for fault tolerance

- Resource Groups = cluster of resources that can be easily manage

- Resource Manager = interface for managing (create, modify, delete) cloud resources

### Core products available in Azure

Compute 

- VM = (IaaS) Virtualization service in azure

- VM Scale Sets = (IaaS) for auto deployment of identical VM

- App Services = (PaaS) for building web apps

- ACI = (PaaS) Container service in azure

- AKS = (PaaS) Kubernetes service in azure

Networking

- Virtual Network = VLAN service connects to VPN

- VPN Gateway = VPN Tunneling service

- Load Balancer = balance network load (layer 4)

- Application Gateway = balance web traffic load  (layer 7)

- CDN = distributed high bandwidth network for faster content delivery (the client will access the nearest server)

Storage

- Blob Storage = for unstructured data storage (Google Drive, OneDirve, Dropbox)

- Disk Storage = for VM disk drives

- File Storage = for NAS like file shares

- Archive Storage = for infrequent accessed unstructured data storage

Database

- CosmoDB = for globally distributed database

- 

Marketplace

- Azure Marketplace = go to place for pre-configured solutions(pfsense, Wordpress, ...)

### Solutions available on Azure

IoT

- IoT Hub = (PaaS) for bi-directional IoT control and monitoring

- IoT Central = (SaaS) for unidirectional IoT monitoring

Big Data Analytics

- Azure Synapse Analysis = for massive parallel processing 

- HDInsight = for managed Hadoop clusters

- Azure Databricks = for Apache Spark analytics

AI

- Machine Learning Service = for AI developers write in python

- Machine Learning Studio = for Noobs with no coding and drag and drop UI

Serverless computing

- Azure Function = for event driven automation executes based on codes

- Logics App = for event driven automation executes based on workflows and has a web GUI

- Event Grid = connects/routes data source to event handlers 

DevOps

- Azure DevOps = for collaborative tools including pipelines, git repositories, Kanban boards and automated load testings

- Azure DevTest Labs = (PaaS) for creating pre-configured development env for DevOps


### Azure management tools

- Azure Portal = web GUI for managing azure

- Azure Powershell = command line interface with powershell commands for managing azure 

- Azure CLI = command line interface with bash commands for managing azure 

- Cloud Shell = terminal in Azure Portal that can use either Azure Powershell or Azure CLI as syntax

Advisor

- Azure Advisor = analyzed deployed services and looks for ways to improve the environment in terms of high availability, security, performance, operational excellence, and cost

## Describe Security, Privacy, Compliance, and Trust (25-30%)

### Securing network connectivity in Azure

- Network Security Groups (NSG) = provide a list of allowed and denied communication to and from network
interfaces and subnets.

- Application Security Groups (ASG) = to define fine-grained network security policies based on workloads, centralized on applications, instead of explicit IP addresses.

- User Defined Rules (UDR) = You can create custom, or user-defined(static), routes in Azure to override Azure's default system routes, or to add additional routes to a subnet's route table.

- Azure Firewall = is a managed, cloud-based, network security service that protects your Azure Virtual Network resources. It is a fully stateful firewall as a service with built-in high availability and unrestricted cloud scalability. Azure Firewall provides inbound protection for non-HTTP/S protocols. Examples of non- HTTP/S protocols include: Remote Desktop Protocol (RDP), Secure Shell (SSH), and File Transfer Protocol (FTP).

- Azure DDoS Protection = protects your Azure applications by scrubbing traffic at the Azure network edge before it can impact your service's availability.

### Core Azure Identity services

- Authentication = who are you

- Authorization = what are you allowed to do

- Azure Active Director = IAM tool for authentication of verified users

- Multi-Factor Authentication = uses multiple things to authenticate an identity of a user (Something you KNOW, Something you HAVE, Something you ARE) ex.(Username and Passcode, RFID Card or OTP, Fingerprint or Face Detect)

### Security tools and features of Azure

- Azure Security Center = unified security management system (Detect, Assess, Diagnose)

- Key Vault = centralized location where you store certificates, and private keys

- Azure Information Protection (AIP) = protects by labelling/classification (Personal, Public, General, Confidential, ...)

- Azure Advanced Threat Protection (ATP) = behavioral monitoring system for users activities

### Azure governance methodologies

- Polices = way to govern users

- Initiatives = group of policies

- Role-Based Access Control (RBAC) = for accessing resources that you only need (Least privilege, Separation of Duty)

- Azure Blueprints = for design of architecture that adhere to certain compliances

Locks

- ReadOnly = cant modify

- CanNotDelete = cant delete

### Describe monitoring and reporting options in Azure

- Azure Monitor = for collecting, analyzing, and acting on logs from your cloud to understand how your applications are performing and identifies issues affecting your resources

- Azure Service Health = suite of experiences that provide personalized guidance and support when issues with Azure services affect you

### Describe privacy, compliance and data protection standards in Azure

 describe industry compliance terms such as GDPR, ISO and NIST

- 

 describe the Microsoft Privacy Statement

- 

 describe the Trust center

- 

 describe the Service Trust Portal

- 

 describe Compliance Manager

- 

 determine if Azure is compliant for a business need

- 

 describe Azure Government cloud services

- 

 describe Azure China cloud services

- 

## Describe Azure Pricing, Service Level Agreements, and Lifecycles (20- 25%)

### Describe Azure subscriptions

 describe an Azure Subscription

- 

 describe the uses and options with Azure subscriptions such access control and offer types

- 

 describe subscription management using Management groups

- 

### Describe planning and management of costs

 describe options for purchasing Azure products and services

- 

 describe options around Azure Free account

- 

 describe the factors affecting costs such as resource types, services, locations, ingress and egress traffic

- 

 describe Zones for billing purposes

- 

 describe the Pricing calculator

- 

 describe the Total Cost of Ownership (TCO) calculator

- 

 describe best practices for minimizing Azure costs such as performing cost analysis, creating spending limits and quotas, using tags to identify cost owners, using Azure reservations and using Azure Advisor recommendations

- 

 describe Azure Cost Management

- 

### Describe Azure Service Level Agreements (SLAs)

 describe a Service Level Agreement (SLA)

- SLA = specific terms that define performance standards

 describe Composite SLAs

- Composite SLA = combination of different SLA's

 describe how to determine an appropriate SLA for an application

- 

### Describe service lifecycle in Azure

 describe Public and Private Preview features

- Public Preview = 

- Private Preview = 

 describe the term General Availability (GA)

- General Availability = 

 describe how to monitor feature updates and product changes

- 

---
### RESOURCES
Online path
https://docs.microsoft.com/en-us/learn/paths/azure-fundamentals/

White paper
aka.ms/azfunpath