# CISSP

# Lesson 1
## Topic 1

CIA Triad
- Confidentiality: Protecting data from unauthorized view
- Integrity: Protecting data from unauthorized modification
- Availability: Ensuring data can be accessed in authorized manner, as permitted

## Topic 2

Security Governance Principles
- Governance: The processes, roles, and policies an organization uses to make decisions
- Security governance: Specific processes, roles, and policies within an organization that enhance security efforts
- Business Impact Analysis (BIA): The overall effort to assess the relative value of assets within the organization, the potential threats to those assets, and possible damage that might be caused if an asset or assets are harmed or lost

Aligning with Business Requirements
- all decisions must be made with the intent of optimizing the organization’s goals

Issues with Mergers/Acquisitions
- Different levels of security, as one entity is less secure than the other which might put the one with higher security at risk

Security Roles and Responsibilities
1. Chief security officer
2. Chief information security officer
3. Security manager
4. Senior management (CEO/President/Owner)
5. IT department personnel
6. Administrators (systems/network/database)
7. Architects
8. Users
9. General counselings
10. Auditors
11. Human Resources personnel

## Topic 3

- Need to know: Information is only disclosed to those who have business need and permission to access it
- Least privilege: Personnel are only given the minimal set of permissions necessary to perform their job function
- Separation of duties: Purposefully imposing inefficiency on business process so that one person cannot complete an entire transaction on their own
- Job rotations: Shifting personnel among various roles throughout the year, for security morale, and continuity purposes
- Due care: The legal duty owed by an organization to its constituents
- Due diligence: Documented efforts demonstrating the organizations activities to provide due care

Privilege Account Management
- Privileged users must be managed in a more restrictive and thorough manner than regular accounts

Information Lifecycle
1. Create
2. Store
3. Use
4. Share
5. Archive
6. Destroy

## Topic 4

Risk Management Concepts
- Risk: Potential harm to an organization
- Threat: A factor that poses risk
- Vulnerability: An avenue that causes or enhances risk

Risk Assessment
- ALE = SLE x ARO
(Annual Loss Expectancy = Single Lose Expectancy x Annual Rate of Occurrence)
(Risk = Consequence x Frequency )

Risk Response
- Acceptance: chooses to accept the risk of an activity
- Avoidance: chooses to cease the activity to remove the risk
- Transference: another party is paid to accept the risk on the organization’s behalf
- Mitigation: risk is reduced through the use of control
//Residual risk: risk that were not eliminated

Types of Control
- Physical
- Administrative
- Logical

## Topic 5

Risk Based Management Concepts to the Supply Chain
- it is important to understand how risks occur, how to frame them, and how to address them

Risk Associated with HW, SW, and Service
- Hardware
- Software
- Service

Third-Party Security Services, Third Party Assessment, and Monitoring
-
//Service-level agreement:

### Risk And Security Control Frameworks

National Standards
- NIST SP 800-37
- NIST SP 800-53
- NIST FIPS 140-2
- NIST FIPS 199

International Standards
- ISO 27000
- COBIT
- CSA STAR
- FedRAMP
- PCI-DSS

## Topic 6

- Security Policy: organizations strategic direction and mandates
- Security Standards: minimum target levels and security practices
- Security Procedures: specific instructions for performing security-related tasks
- Security Guidelines: recommendations for security practices

## Topic 7

Securely Provisioning Resources
- asset inventory: a tool or method for teaching all assets within the organization
- identification and tracking of assets
- user is liable and responsible

Change Management Processes
- Configuration management: used to determine baseline settings and version of assets in the inventory
- Change management: used to modify the configuration of assets in the inventory

Resource Protection Techniques
- should be familiar with standard practices for protecting assets such as controls that mitigate exploits
//Hardening: protection of assets from being misused or exploited
- Removing default accounts
- Removing unnecessary services
- Installing anti-malware or control tools
- Increasing logging

Appropriate Asset Retentions
- maintain assets for an appropriate length of time
- assets will be stored in archive until the retention period is reach
- at the end of the retention period the asset must be disposed in a secure manner

## Topic 8

- it is crucial for an organization to identify all assets under its control
- all assets should be assigned a classification level
- classification should be assigned as soon as the assets is acquired and should be updated throughout the asset’s life cycle

Information and Asset Handling Requirements
- processes, procedures and measure used to securely handle assets

## Topic 9

Determine Data Security Control
- Cost: price of control for securing data. Should include both the price of acquiring the control and long-term cost of operating, monitoring and maintaining the control
- Standards: assets will be governed by particular regulations and other mandates typically relevant standards
- Data state: data at rest, data in motion, and data in use. You should be familiar in how data is processed in various stages
- System requirements: data resides in different systems such as servers, endpoints, and etc. You should be familiar with the controls that are effective in protecting data from these systems

Data Protection Methods
- Encryption
- Data security solutions such as firewalls, intrusion prevention systems, database activity monitors, and etc
- Egress monitoring (Data Loss Prevention)
- Additional access control mechanism for files (Data Rights Management/ Information Rights Management )
- Integrity Check mechanism
- Masking
- Policy
- Digital signatures
- Legal protections
- Tokenization

## Topic 10

Enforce Personnel Security Policies and Procedures
- role in developing, reviewing, and enforcing personnel security policies
- aware of and deal with personnel security aspects which have significant bearing on the overall security of the organization

Personnel Security Policies
- Hiring and termination process
- Personnel protection during emergencies
- Acceptable use policy
- Nondisclosure agreements
- Travel security
- Executive programs
- Personnel access control
- Education/training programs
- Vendor/consultant.contractor agreements/policies for limited access employment
- Privacy

Establish and Maintain a Security Awareness Education, and Training Program
- the difference between education, training, and awareness (SETA)
- when instruction should be applied
- methods for conveying information
- ways to collect instructions
//GOAL: reducing risk to the organization, enhancing personnel safety, and reducing liability

Address Personnel Safety and Security Concerns
- Emergency situations: should be informed as how to respond to emergencies
- Travel security: policies and procedures need to account the personnel’s safety while on mobile

# Lesson 2
## Topic 1

### OSI and TCP/IP Models

OSI
1. Physical: Networking cables like Fiber optics, Twisted pair, Coaxial, Wireless
2. Data Link: Network Interface Cards (NIC), MAC address, Bridges and switches
3. Network: IP, IP address, Router, some firewalls
4. Transport: TCP, UDP, some firewalls
5. Session: Formally creates, maintain sessions, RPC
6. Presentation: ASCII, Unicode
7. Application: Telnet, FTP, SNMP, HTTP, some firewalls

TCP/IP
1. Link: Ethernet, TokenRing, Frame Relay, ATM
2. Internet: IP, ARP, ICMP, IGMP
3. Transport: TCP, UDP
4. Application: Telnet, FTP, SMTP, DNS, RIP, SNMP

IP Networking

SYN -> SYN+ACK -> ACK

LISTEN -> SYN RECEIVED -> ESTABLISHED

Vulnerabilities of Security Architectures
- Client/Server systems:
- Distributed systems:
- ICS/IOT/Embedded systems:
- Web Based systems:
- Mobile Systems:
- Content distribution networks (CDN):
- Databases:
- Cloud Computing:

## Topic 2

Implement Secure Communication Channels According to Design
- Secure methods and practices should be included in the design of a system(within networks, between networks, over a variety go communication media)

Secure Data Communications
- Network Segmentation: divides the big network into various smaller networks
- Virtual Local Area Network (VLAN): network created through logical addressing
- Software-Defined Networking (SDN): an approach to networking that abstracts the hardware involved in communication away from the design and control of the overall network

Data Plane: Hardware Devices

Control Plane: Controllers/APIs

Application Plane: Applications
- Encryption: obscure data through the use of a defined and reversible process

Secure Remote Access
- Remote Access: refers to the practice of allowing external parties to communicate with a particular network
- Virtual Private Network (VPN): is an encrypted tunnel that creates a secure, temporary connections between an external user and the network
- VPN uses tunneling protocols such as PPTP(Point to Point Tunneling Protocol), L2TP(Layer 2 Tunneling Protocol) or IPsec

Collaboration and Convergence
- Collaboration: a practice of working with someone to create something
- Convergence: a practice of using one communication medium to convey multiple forms of communication

Wireless Networking
- Risk: intermediaries (Man-in-the middle attack)
- Threats: External attacker might try to harvest communication within the networked environment
- Security: wireless should utilize strong encryption (WPA2) with Advanced Encryption Standards

## Topic 3

- Trusted Platform Module (TPM): to verify the integrity go a given system with a unique cryptographic key burned onto an integral chipset
- Hardware Security Module (HSM): tamper resistant crypto-processor designed for the generation, management and distribution of cryptographic keys
- Security Kernel: element of hardware, firmware, and OS that enforce the reference monitor concept
- Memory Protection: where the system assigns and isolate areas of primary storage for specific programs

System Basis
- CPU
- RAM
- ROM
- Firewall
- OS
- Storage

Transmission Media
- Twisted Pair: composed of pairs of twisted copper wires
- Coaxial Cable: insulated copper wires
- Fiber Optic: spun glass or plastic that conveys data via light
- Wireless: electromagnetic waves

## Topic 4

Firewalls
- are devices typically used to monitor inbound traffic but they can sometimes monitor bidirectional traffic as well
- Layer 3,4, and 7
- detect using content filtering, static packet inspection, stateful inspection, and behavioral monitoring

Intrusion Detection or Prevention systems (IDS/IPS)
- inside the network to detect and determine if a successful penetration has occurred
- detect using known signatures of attacks, statistical analysis, and behavioral monitoring

Whitelisting/Blacklisting
- Whitelist: prohibitive
- Blacklist: permissive
- Better to block all traffic except trusted entities

Sandboxing
- refers to the practice of abstracting contact with underlying hardware, instead constraining programs to run in a restricted environment that provide resources at a remove
- virtual machine is a form of sandboxing

Honeypots/Honeynets
- are simulated environments/components that contain no raw production data
- the intent of these devices is to distract attackers from actual valuable materials

Antimalware
- are intended to inhibit, detect, quarantine, and remove malware targeting the environment
- also offers identity management and network monitoring

## Topic 5

Implement and Support Patch and Vulnerability Management
- Patches: are updates to the existing IT environment and typically it is intended to fix security flaws or enhance performance
- - Routine patches: regularly scheduled events with low threshold of criticality
- - Reactive patches: are created in response of recent discovered threat or vulnerability

Challenges in patching:
- Interoperability
- Poorly crafted patches
- Required downtime
- Added expense
- Virtualization-specific concerns
- Timing

Standard patching process:

# Lesson 3
## Topic 1

Incident Management
1. Detection: discovering that an incident may have taken place
2. Response: determining whether the reported activity is truly an incident, is underway, or has occurred
3. Mitigation: immediate action taken upon determining an incident had occurred
4. Reporting: after mitigation the incident needs to be assessed, analyzed, and reported to any other relevant stakeholders
//Senior management will decide how the organization should proceed
5. Recovery: proceed to return the environment to normal operations
6. Remediation: after a returning normal operations, the root cause of incident should be addressed
7. Lesson Learned: It is useful for the organization to have a detailed report on the incident for future use


Variables affecting how an incident is initially addressed:
- Time
- Risk
- Impact

Detection
- Intrusion detection system
- Antimalware solutions
- Log analysis
- Firewalls
- Vulnerability scan solutions
- Database activity monitors
- Data leak protection
- Digital rights management

## Topic 2

What is the critical path?

How long can the organization survive an interruption of the critical path?

How much data can the organization lose and still remain viable?

Identify, Analyze, and Prioritize Business Continuity Requirements
- Business Continuity (BC): Actions, processes, and tools for ensuring an organization can continue critical operations during contingency
- Maximum Allowable Downtime (MAD): referred to as the maximum tolerable downtime
//is the measure of how long an organization can survive an interruption of critical functions
- Recovery Time Objective (RTO): is the target time set for recovering an interruption
- Recovery Point Objective (RPO): is a measure on how much data the organization can lose before the organization is no longer viable
- Business Impact Analysis (BIA): is the effort required to determine the value of each asset belonging to the organization, as well as the potential risk of losing assets

Ways on conduction BIA and asset value determination:
- Survey: Interview asset data to determine their value
- Financial Audit: Review acquisition documentation to aggregate the value of an asset
- Customers Response: can determine which aspect of the operation are most valuable

Backup/Recovery Concepts
- Onsite: the organization has full control of stored data
- Offsite: the organization loses some control of the security governance and controls used to store data
- Full: all data in the environment is copied
- Differential: all data in the environment that has changed since the last backup is copied
- Incremental: all data in the environment that has changed since last backup is copied

Recovery Site Strategies
- Hot: fully functional operation site
- Warm: like hot set but does not have the current version of the organization data
- Cold: empty facility and is not active
- Mobile: portable facility
- Cloud: backup data is stored with a cloud computing service provider
- Joint operating agreement (JOA): contractual techniques for creating alternate operation location
- Multiple processing sites: geographically separated production sites

System Resilience, High Availability, Quality of Service, and Fault Tolerance
- Resource clustering
- Power redundancy (UPS, Generator)
- RAID
- Centralized data storage (NAS)

Testing BCDR Plans
- Read Through/Tabletop: role playing activity that only involves a moderator and personnel tasked with DR
- Walk Through: participants go to each of the need location for the response activity
- Simulation: involve all personnel working in the site
- Parallel: utilize alternative site
- Full Interruption: scripted simulation that mimics an actual contingency event

# Lesson 4
## Topic 1

Design and Validate Assessment, Test, and Audit Strategies
- help determine the extent to which security controls are implemented correct by the organization security policy
- Internal Assessment: are controls that are associated with authorized and trusted actors and the threat that may stem from misuse of resources
- External Assessment: focus on threats by external actors that seek unauthorized access to organizational resources
- Third party Assessment: provide auxiliary support to internal and external testing methodologies

Types of Assessments
- Vulnerability scans:
- Penetration Tests: attempt to explode vulnerabilities
- Audits: are reviews of an environment in order to determine compliance with a standard
- Log reviews: logs monitoring
- Synthetic transaction: tests that feature the use of automated agents to simulate user interaction
- Code review and testing: process of determining that software development efforts are using correct methods and successfully incorporating security in the product
- Misuse case testing: test that involves purposefully using known bad functions in order to determine the stability if the system
- Test coverage analysis: reviewing test methods and the target determines how much the code or how many path of the system functions have been tested
- Interface testing: reviewing user interactions with the target ensure security

Test Analysis and Reporting
- it should be verified that the access control procedures utilize in production procedures are used in testing procedures

Scoping/Tailoring
- Scoping: is the practice of choosing which element of the enterprise should be included in a particular assessment
- Tailoring: is the practice of applying only the measures that would be beneficial to a situation

Account Management
- Assign account managers for information system accounts
- Establish conditions for group or role membership
- Specify authorized users
- Require approval for authorizations
- Monitor use of accounts
- Review account compliance

Management Review and Approval
- periodic management review ensure that security process data is being used as intended

Key Performance and Risk Indicators
- KPI: looking to the past
- KRI: looking to the future

Backup Verification
- backup plan should have supporting documentation that contain procedures for proper restoration of data

Training and Awareness

Important personnel that is involved:
- Executive management
- Security personnel
- System owners
- System administrators and IT support personnel
- Operational managers and system users

## Topic 2

Conduct Logging and Monitoring Activities
- the organization has to record and analyze enterprise events and traffic
- should be familiar with common logging methods, solutions, and best practice

Intrusion Detection and Prevention
- Intrusion Detection System (IDS): is a solution that monitors the environment and automatically recognize malicious attempt to gain unauthorized access
- Intrusion Prevention System (IPS): is a solution that monitors the environment and automatically takes action when it recognize malicious attempt to gain unauthorized access

Tradeoffs Associated with IDS/IPS
- Maintenance: system still needs regular maintenance regardless of IDS and IPS
- Overhead: IDS and IPS will have an impact in production so the organization will need to limit it on high value assets
- False Positive: sometimes security tools might respond a legitimate transaction to an actual attack

Typical SIEM Solutions
- Aggregation: gather information across the environment like logs from firewalls, IDS/IPS, network devices
- Normalization: collect different types of information from different types of sources and present the data in a meaningful and standardized way for analysis
- Correlation: mathematically assigns weight and probability to various activities given a stream of logs on an actual acctact
- Secure storage: have the ability to archive materials in a secure

# Lesson 5
## Topic 1

Control Physical and Logical Access to Assets
- assets must be protected from unauthorized view, modification, and removal
- Identification and Access Management (IAM): limiting the capability to affect assets to only those entities with permission
- Physical controls: physically protects assets from unauthorised access
- Logical controls: limit unauthorized activity in the IT environment

Manage Identification and Authorization
- Identification: Assign a unique value to every person or device that will access the environment
- Authentication: a method of verifying that the entity presenting an identity assertion is valid
- Authorization:set of permissions granted to a specific entity upon the receipt of an authenticated identity
- Accountability: attribute every action to a specific entity

For sensitive data multi factor authentication is highly advised
- Something you know (Passwords, Combinations)
- Something you have (Physical key, RFID)
- Something you are (Biometrics)

## Topic 2

Manage the Identity and Access Provisioning
- Account access: is the combination of identity assertion and account credentials
- Provisioning: identity of the entity is validated
- Management: data owner who granted the employee access should review accounts on regular basis to determine if all accounts currently need to have access permissions
- Deprovisioning: account is locked or has its access revoked

Identity Federation
- single sign-on user: a user has one set of credential that allows access to multiple systems in a single organizations

Session Management
- sessions must be formally end or else there’s a risk of an attacker using validated session credentials

## Topic 3

Security Models
- Bell-LaPadula
- Biba
- Graham-Denning
- Brewer-Nash
- Clark-Wilson

Bell-LaPadula
- intended to address confidentiality in a multilevel security system
- defines primary security constructs
- subjects: are active parties
- objects: are passive parties
- This model defines who properties:
- - Simple Security: subject cannot read an object of higher classification
- - Star: subject can only save an object at the same or higher classification

Biba
- designed to address data integrity and does not address data confidentiality
- use observe and modify
- This model defines who properties:
- - Simple Integrity: subject cannot observe an object of lower integrity
- - Star: subject cannot modify an object of higher integrity
- - Invocation: subject cannot send logical service request to an object of higher integrity

Brewer-Nash
- focus on preventing conflicts of interest when a given subject has access to objects with sensitive information
Clark-Wilson
- focus on integrity of the transaction level and addressing three major goals of integrity
- authorized access is evaluated by a third party

Graham-Denning
- concerned with how subject and objects are created, how it is assigned rights and privileges and how it is managed

Authorization Models
- Role-based Access Control (RBAC)
- Rule-based Access Control (RBAC)
- Mandatory Access Control (MAC)
- Discretionary Access Control (DAC)
- Attribute-based Access Control (ABAC)

Role-based Access Control
- is an access control policy that restricts information system access to authorized users

Rule-based Access Control
- based on predefined list of rules that can determine access controls

Mandatory Access Control
- access control policy decisions are made by a central authority and not by the individual owner of an object

Discretionary Access Control
- leaves a certain amount of access control to the discretion go the object owner or authorized controller

Attribute-based Access Control
- is an access control paradigm whereby access rights are granted to users with policies that combine attributes

# Lesson 6
## Topic 1

Understand and Integrate Security in the Software Development Lifecycle (SDLC)
- to ensure development success, organizations must have appropriate software development lifecycle methodologies to guide them

OWASP Top 10 Projects
- Injection: occurs when an attacker enters executable code into a data field and the program runs the command
- Broken Authentication: incorrect implementation of application access control function can lead to loss of user credentials
- Sensitive Data Exposure: web applications may expose sensitive data
- XML External Entities: many older or poorly configured XML processors evaluate external entities references within XML documents
- Broken Access Control: user permission are not properly enforced
- Security Misconfiguration: an attacker could exploit misconfigured components/systems
- Cross-Site Scripting: an attacker can exploit API functionality that insert untrusted data into a new web page into the user’s browser
- Insecure Deserialization: often leads to remote code execution
- Using Components with Known Vulnerabilities: a programmer is unaware of risks associated with specific programming components
- Insufficient Logging and Monitoring: coupled with missing or ineffective integration with incident response, allows attackers to further attack systems, and tamper, extract, or destroy data

SDLC Models
- Waterfall: it represents a phased approach to software development where each phase is completed before the next one can be started
- Spiral: is a nested version of waterfall method, and the development of each phase is carefully designed which include risk analysis and assessment
- DevOps: is a combination of participants from various functions areas (development, production, security, quality assurance, management, etc.) involved in the overall development effort , intended to ensure all functional and nonfunctional requirements are met during development
- Agile: are results-driven approach that focus on early delivery and continual optimization of software as opposed to concentration on contract renegotiation and documentation

Configuration/ Change Management (CM)
- refers to monitoring and managing changes to a program
- the goal is to guarantee the integrity of the code, availability, and usage of the correct version of all systems components

Identity and Apply Security Controls in Development Environments

Software must be protected to ensure:
- it does not include vulnerabilities
- secure source code
- unfinished software does not affect the production environment

## Topic 2

Assess the Effectiveness of Software Security
- Static Application Security Testing (SAST): white box testing or secure code review, involves using methods and tools to review the actual source code of an application, locating known security problems and vulnerabilities
- Dynamic Application Security Testing (DAST): black box testing or play testing, the application is actually executed and testers perform functions with the application runtime state, trying to determine if the software can successfully perform required functionality but also attempt to find situations in which the software fails

Threat Modeling
- Spoofing
- Tampering
- Repudiation
- Information Disclosure
- Denial of Service
- Elevation of privilege

Application Programming Interface (API) Security
- are set of rules, tools, and languages used by programmers to simplify the creation of software
- the term API describe the use of applications that operate across organizations often via web an often involving end user participation

Access Security Impact of Acquired Software
- it is important to understand the need for security during the purchase and implementation of software that has been sourced from outside the organization

# Lesson 7
## Topic 1

Legal and Regulatory Issues that Pertain to Information Security in a Global Context
- Jurisdiction: geographic area that a given legal body claims control of
- Transborder data flow: some jurisdictions prohibit certain types of information from leaving the confines of a jurisdiction
- Import/Export restrictions: some jurisdictions limit specific technologies from entering or leaving the confines of a jurisdiction
- Intellectual properties: these are intangible assets: literary property of the mind
- Licensing: intellectual properties is often accessed through the means of a license
- Digital rights management (DRM): this is a technological control for protecting intellectual property and sensitive data usually at the file level
- Data reminisce: this includes any data that may be still be recovered from media after deletion action has been taken
Privacy
- is the idea that an individual person should be able to determine the distribution and dissemination of all data that identifies that person
- Personally Identifiable Information (PII): these includes data the can be used to determine the identity of an individual
- Roles:
~Subject: the person identified by the PII
~Data controller: the entity collection PII
~Processing: anything that can be done to data
~Data processor: any entity that performs data processing on behalf of the data controller

Privacy Law Principles
- Notification: the subject must be told told of the collection and allowed to end the transaction instead of disclosing PII
- Specification: the subject will be told the purpose of the collection if that purpose changes the subject must be notified again and allowed to end the transaction
- Collection Limitation: only the PII required for the transaction will be harvested which will be done by fair and legal means
- Openness: the subject will be allowed to access any of their own PII
- Accuracy: the subject will be allowed to correct any of their own PII
- Security: the data controller will be legally responsible for protecting any PII it collects
- Use Limitation: the data owner will not use the PII in any way other than what was specific to the subject
- Accountability: the data controller will be legally responsible for the loss of any PII it collects
Determine Compliance Requirements
- Compliance: is the condition of adhering to all mandates, rules, and obligation
- Legal/Regulatory: external mandates from governments that address all organizations in a jurisdiction in a specific industry
- Standards:standards outline best practices for particular actions/procedures; standards can b e created internally or externally
- Contractual: parties to a contract typically have the rights to determine that the other party are adhering to the terms

### Privacy Laws EU:

General Data Protection Regulation (GDPR)
- EU law that threats personal data as a human rights and prohibits EU citizen data from being stored in any country that does not have national personal privacy laws

### Privacy Laws USA:

Health Insurance Portability and Accountability Act (HIPAA)
- federal law with privacy elements applicable only to medical providers and their business partners

(GLBA)
- federal law with privacy elements applicable only to insurers and banks

(FERPA)
- federal law that deals specifically with personal privacy applies only to schools

(COOPA)
- federal law that deals specifically with the personal privacy of children’s applies only to online service

## Topic 2

Understand Requirements for Investigation Types
- Administrative: the organization is investigating a violation of its own policies: the investigation is performed by staff, employees, or contractors of the organization itself. The management determines the outcome
- Civil: the organization is party to lawsuit and must gather evidence for litigation. A court will determine the outcome
- Criminal: the organization or a member of it is under investigation for illegal action. A court will determine the outcome
- Regulatory: the organization is investigated for noncompliance with regulatory mandates A regulator will A court will determine the outcome

Evidence Collection and Handling
- all materials associated with an incident could be pertinent to an investigation and used as evidence

This includes:
- Data that have been compromised
- Systems that have been compromised
- Data about the incident
- Information from people with knowledge of the incident
- Information about the incident scene

Reporting and Documentation
- all relevant information must be documented and catalogued for presentation
- Admissibility: only evidence that is acceptable to the court may be presented
- Accuracy: the evidence should be true and clear
- Comprehensibility: even though the organization is trying to present one particular story the organization cannot withhold evidence that may be contrary to the story
- Objectivity: the evidence should stand for itself on a factual basis

Investigation Techniques
- Automated capture: the organization’s monitoring activity can be used for collection and analyzing incident data in addition to the goals of detection and performance optimization
- Interviews: you can solicit information from the people involved with or who have insight into an incident
- Manual capture: the investigator can make copies of evidence where necessary and then record specific information for later usage
- External requests:investigators can request information from external sources to collect evidence relevant to the situation

Digital Forensics Tools, Tactics, and Procedures
- Document everything
- Avoid unrecorded modification
- Collection is a sensitive process
- It is not an amateur endeavor

## Topic 3

Code of Ethics

https://www.isc2.org/Ethics

Preamble
- The safety and welfare of society and the common good, duty to our principles, and to each other, requires that we adhere, and be sees to adhere, to the highest ethical standards of behavior.
- Therefore, strict adherence to this Code is a condition of certification. For our clientele, and the public at large, to see the value in certifications, they must be able to trust our members; this trust must come from a belief that members act in a manner that is correct and professional and offer benefit.
The ISC member is expected to do the ff:
- Protect society, the common good, necessary public trust and confidence, and infrastructure
- Act honorably, honest, justly, responsible, and legally
- Provide diligent and competent service to principles
- Advance and protect the profession
