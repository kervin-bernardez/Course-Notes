# AZ 900 Microsoft Fundamentals

## Describe Cloud Concepts

### Describe the benefits and considerations of using cloud services

 describe terms such as High Availability, Scalability, Elasticity, Agility, Fault Tolerance, and Disaster Recovery

- High Availability = service accessibility

- Scalability = allows to increase or decrease resources horizontally(UP) or vertically (DOWN)

- Elasticity = allows to increase and decrease resources IN or OUT

- Agility = ability to rapid deploy

- Fault Tolerance = ability to operate while experiencing failure

- Disaster Recovery = ability to recover from large scale disruptions

 describe the Principles of Economies of Scale

- Economies of Scale = do things more efficiently at lower cost at large scale

 describe the differences between Capital Expenditure (CapEx) and Operational Expenditure (OpEx)

- CapEx = tangible resources

- OpEx = intangible resources

 describe the Consumption-based Model

- Consumption-based Model = pay-as-you-go

### Describe the differences between Infrastructure-as-a-Service (IaaS), Platform-as-a-Service (PaaS) and Software-as-a-Service (SaaS)

 describe Infrastructure-as-a-Service (IaaS)

- IaaS = manages VM and OS (Ubuntu, CentOS, ...)

 describe Platform-as-a-Service (PaaS)

- PaaS = manages a service (Pfsense, OpenVPN, ...) without worrying about the VM and OS

 describe Software-as-a-Service (SaaS)

- SaaS = manage only the software (GSuites, Office 365, ...)

 compare and contrast the three different service types

- 

### Describe the differences between Public, Private and Hybrid cloud models

 describe Public cloud

- Public cloud = third-party managed cloud for lease (Azure, AWS, GCP)

 describe Private cloud

- Private cloud = privately managed cloud resources (Nextcloud, OwnCloud, ...)

 describe Hybrid cloud

- Hybrid cloud = combination of public and private cloud

 compare and contrast the three different cloud models

## Describe Core Azure Services

### Describe the core Azure architectural components

 describe Regions

- Regions = location of data centers

- Region Pairs = 300 miles apart data center paired for disaster recovery

 describe Availability Zones

- Availability Zones = protection from entire data center failure for fault tolerance

- Availability Sets = protection from rack failure for fault tolerance

 describe Azure Resource Manager

- Resource Manager = interface for managing (create, modify, delete) cloud resources

 describe Resource Groups

- Resource Groups = cluster of resources that can be easily manage

 describe the benefits and usage of core Azure architectural components

-

### Describe some of the core products available in Azure

 describe products available for Compute such as Virtual Machines, Virtual Machine Scale Sets, App Services, Azure Container Instances (ACI) and Azure Kubernetes Service (AKS)

- VM = (IaaS) Virtualization service in azure

- VM Scale Sets = (IaaS) for auto deployment of identical VM

- App Services = (PaaS) for building web apps

- ACI = (PaaS) Container service in azure

- AKS = (PaaS) Kubernetes service in azure

 describe products available for Networking such as Virtual Network, Load Balancer, VPN Gateway, Application Gateway and Content Delivery Network

- Virtual Network = VLAN service connects to VPN

- VPN Gateway = VPN Tunneling service

- Load Balancer = balance network load (layer 4)

- Application Gateway = balance web traffic load  (layer 7)

- CDN = distributed high bandwidth network for faster content delivery (the client will access the nearest server)

 describe products available for Storage such as Blob Storage, Disk Storage, File Storage, and Archive Storage

- Blob Storage = for unstructured data storage (Google Drive, OneDirve, Dropbox)

- Disk Storage = for VM disk drives

- File Storage = for NAS like file shares

- Archive Storage = for infrequent accessed unstructured data storage

 describe products available for Databases such as Cosmos DB, Azure SQL Database, Azure Database for MySQL, Azure Database for PostgreSQL, Azure Database Migration service

- CosmoDB = for globally distributed database

- 

 describe the Azure Marketplace and its usage scenarios

- Azure Marketplace = go to place for pre-configured solutions(pfsense, Wordpress, ...)

### Describe some of the solutions available on Azure

 describe Internet of Things (IoT) and products that are available for IoT on Azure such as IoT Hub and IoT Central

- IoT = internet connected smart devices

- IoT Hub = (PaaS) for bi-directional IoT control and monitoring

- IoT Central = (SaaS) for unidirectional IoT monitoring

 describe Big Data and Analytics and products that are available for Big Data and Analytics such as Azure Synapse Analytics, HDInsight, and Azure Databricks

- Big Data Analytics = large volume of data for data science

- Azure Synapse Analysis = for massive parallel processing 

- HDInsight = for managed Hadoop clusters

- Azure Databricks = for Apache Spark analytics

 describe Artificial Intelligence (AI) and products that are available for AI such as Azure Machine Learning Service and Studio

- AI = smart automation or machine learning

- Machine Learning Service = for AI developers write in python

- Machine Learning Studio = for Noobs with no coding and drag and drop UI

 describe Serverless computing and Azure products that are available for serverless computing such as Azure Functions, Logic Apps, and Event Grid

- Serverless computing = runs code completely abstract from the hosting infrastructure

- Azure Function = for event driven automation executes based on codes

- Logics App = for event driven automation executes based on workflows and has a web GUI

- Event Grid = connects/routes data source to event handlers 

 describe DevOps solutions available on Azure such as Azure DevOps and Azure DevTest Labs

- DevOps = development and operations for software life cycle uses agile methodologies

- Azure DevOps = for collaborative tools including pipelines, git repositories, Kanban boards and automated load testings

- Azure DevTest Labs = (PaaS) for creating pre-configured development env for DevOps

 describe the benefits and outcomes of using Azure solutions

### Describe Azure management tools

 describe Azure tools such as Azure Portal, Azure PowerShell, Azure CLI and Cloud Shell

- Azure Portal = web GUI for managing azure

- Azure Powershell = command line interface with powershell commands for managing azure 

- Azure CLI = command line interface with bash commands for managing azure 

- Cloud Shell = terminal in Azure Portal that can use either Azure Powershell or Azure CLI as syntax

 describe Azure Advisor

- Azure Advisor = analyzed deployed services and looks for ways to improve the environment in terms of high availability, security, performance, operational excellence, and cost

## Describe Security, Privacy, Compliance, and Trust 

### Describe securing network connectivity in Azure

 describe Network Security Groups (NSG)

- NSG = provide a list of allowed and denied communication to and from network
interfaces and subnets.

 describe Application Security Groups (ASG)

- ASG = to define fine-grained network security policies based on workloads, centralized on applications, instead of explicit IP addresses.

 describe User Defined Rules (UDR)

- UDR = You can create custom, or user-defined(static), routes in Azure to override Azure's default system routes, or to add additional routes to a subnet's route table.

 describe Azure Firewall

- Azure Firewall = is a managed, cloud-based, network security service that protects your Azure Virtual Network resources. It is a fully stateful firewall as a service with built-in high availability and unrestricted cloud scalability. Azure Firewall provides inbound protection for non-HTTP/S protocols. Examples of non- HTTP/S protocols include: Remote Desktop Protocol (RDP), Secure Shell (SSH), and File Transfer Protocol (FTP).

 describe Azure DDoS Protection

- Azure DDoS Protection = protects your Azure applications by scrubbing traffic at the Azure network edge before it can impact your service's availability.

 choose an appropriate Azure security solution

- 

### Describe core Azure Identity services

 describe the difference between authentication and authorization

- Authentication = who are you

- Authorization = what are you allowed to do

 describe Azure Active Directory

- Azure Active Director = IAM tool for authentication of verified users

 describe Azure Multi-Factor Authentication

- Multi-Factor Authentication = uses multiple things to authenticate an identity of a user (Something you KNOW, Something you HAVE, Something you ARE) ex.(Username and Passcode, RFID Card or OTP, Fingerprint or Face Detect)

### Describe security tools and features of Azure

 describe Azure Security Center

- Azure Security Center = unified security management system (Detect, Assess, Diagnose)

 describe Azure Security Center usage scenarios

- 

 describe Key Vault

- Key Vault = centralized location where you store certificates, and private keys

 describe Azure Information Protection (AIP)

- AIP = protects by labelling/classification (Personal, Public, General, Confidential, ...)

 describe Azure Advanced Threat Protection (ATP)

- ATP = behavioral monitoring system for users activities

### Describe Azure governance methodologies

 describe policies and initiatives with Azure Policy

- Polices = way to govern users

- Initiatives = group of policies

 describe Role-Based Access Control (RBAC)

- RBAC = for accessing resources that you only need (Least privilege, Separation of Duty)

 describe Locks

- ReadOnly = cant modify

- CanNotDelete = cant delete

 describe Azure Advisor security assistance

- 

 describe Azure Blueprints
- Azure Blueprints = for design of architecture that adhere to certain compliances

### Describe monitoring and reporting options in Azure

 describe Azure Monitor

- Azure Monitor = for collecting, analyzing, and acting on logs from your cloud to understand how your applications are performing and identifies issues affecting your resources

 describe Azure Service Health

- Azure Service Health = suite of experiences that provide personalized guidance and support when issues with Azure services affect you

 describe the use cases and benefits of Azure Monitor and Azure Service Health

- 

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

## Describe Azure Pricing, Service Level Agreements, and Lifecycles

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