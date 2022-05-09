Avanade Velocity 2022


https://www.techtarget.com/whatis/
# Cloud Concepts
- Cloud computing- computing serives over internet 
- Compute, Networking, storage, analytics
- Basically, sotring your stuff on someone else's server
- PAYG

# Public Cloud
- e.g. Azure, AWS
- Owned by cloud services
- Shared, used by others

# Private Cloud
- you need to pay for everything yourself
- no access to users outside organisation
- Organisation creates cloud environment in their on-prem DB

# Hybrid
- Private + public

# Benefits
- High Availability: high uptime. Minimum is 2 nines (3.65 days a year)
- Fault-tolerance: can offer this as Microsoft has a global reach.
- Scalability and Elasticity- can scale up, out, in and only pay for what you use.
- Customer Latency Capabilities: Because of global reach, you can access the data whereever you are
- Agile: can delete what you don't want
- Disaster Recovery: can fail over from one region to another (if something happens in VM in one region for example, it will fail over to another region)
- Security: Microsoft have their certifications

# IaaS
- Compute, networking and storage are managed for you
- You manage everything else 

# PaaS
- Runtime, OS, VM, Compute, networking, storage are managed for you.
- You only manage Applications and Data + Access

# SaaS
- Applications, Runtime, OS, VM, Compute, networking, storage are managed for you.
- You only manage Data and Access


# Serverless Computing
- PaaS but you need even less to work with
- Azrue Logic Apps = if this then that apps
- Azure Function allows you to bring code into the logic apps. It is the code running your services
- Need to write our code to Azure
- Ability to execute code without generating a monolithic environment

# Core Azure Services
- There are over 10,000 items in Azure market place and over 2,000 services
-
## Core Architectural pairings:
### Regions:
- go to the website with globe on it to see regions
 - Regions are made up of one or more datacentres in close proximity e.g UK sounth/UK west
 - In each region are Locations e.g. Cardiff/London
 - In each location are Zones (region is made up of one or more zones)
 - Zones are made up of one or more data centres
 - Data cebtres are made up of racks

 ### Region Pairs:
 - At least 3 hundreds of miles of seperation between region pairs
 - Automatic replication for some services
 - Prioritised region recovery in the event of outage
 - e.g. East US -> West US, UK West -> UK South
 - Updates are rolled out in one pair first, then the other. This minimises downtime.


 ## Azure Resources
 - VM
 - Storage Accounts
 - App Services
 - SQL Database
 - Functions
 - Logic Apps

 ## Resource Groups
 - First you get a subscription. This gives you a scructure
 - Azure Resource Manager (ARM) dictates what structure you have. Everything you build starts at the bottom of this structure (ResourceGroup)
 - Everything starts with a resourceGroup. You create multiple resource groups. Then create 'stuff'e.g. a VM in the resource group (According to ARM, everything must be built in a resource group). Resources can exist in only one resource group
 - A resource group is like a folder to **manage** the resources
 - Resources can be created in different regions
 - Resources can be moved in different resource groups
 - Can't put resource groups inside other resource groups

 ## Azure Virtual Machine
 - IaaS offering that provides total control and customization

 ## App Services
 - works with .net, .net core, node.js, java, python, php
 - writing code to the cloud

 ## Big Data and analytics
 - Azure Synapse Analytics- data analytics, data warehouse
 - Azure HDInsight-open source analytics service for enterprises
 - Azure Databricks- structuring of data

 ## AI and ML
 - Azure machine learning: cloud based to develop, train, deploy ML models
 - Cognitive Services: enable an app to see, her, speaj, interpret a user's need
 - Bot Service: develop intelligent bots

 ## Azure Management Tools
 - Azure portal, Azure Poweshell, Azure CLI, Cloud Shell, Azure Mobile App etc
 - ANything that uderstands ARM

 ## ARM Templates
 - whatever language you use, it always speaks to ARM using JSON files.
 - Declarative syntax -> either Yes or No, 1 or 0, On or Off, Do or Do Not. No ambiguity

 ## Azure Advisor
 - Analyses deployed resources and makes recommendations based on best practices (reliability, security, performance, cost, operational excellence)


 ## Azure Monitor
 - Generates logs and gives application insights.
 - Gives customised dashboards

 ## Azure Service Health
 - Tells you if there are any problems, outages etc.
 - status.azure.com shows if there is anything down

 # Security
 ## Microsoft Defender for Cloud
 - Monitoring service that provides threat protection across Azure and on-remise datacentres
 - provides security recommendations, detects and blocks malware, identifies potential attacks
 - Does not actually do anything about the information it gathers
 ## SIEM - Sentinel
 - Security Information and Event Management
- This actually does something about security risks

--- Make sure when writing code that it can be fed into these security services ---

## Azure Key Vault
- stores application secrets in a centralised cloud location to securely control access permissions and access logging

## Azure Dedicated Host
- Provides **physical** servers that host one or more Azure Virtual Machines that is dedicated to a single organisation's workload
- Benefit= hardware isolation - nobody else is using that piece of hardware. Also, you get to choose when maintenance and updates take place

## Defense in depth
- A layered approach to secure computer systems, provides multiple levels of protection
- Industry standard way of making sure everyone that is dealing with the data knows that we have multiple levels of security/protection.
- Physical security > identity and access > permiter > network > compute > application > data

## Network Security Groups
- Filters network traffic

## Azure Distributed Denial of Service (DDoS) protection
- DDoS attacks overwhelm and exhaust network resources, making apps slow or unreponsive
- Never confirms the session, goes in a loop

# Identity, governance, privacy and compliance
- making sure you correctly control access to data
- Authentication - who are you?
- Authorisation - what can you do?
- Azure Multi- Factor Authentication (something you know, something you possess, something you are)
- Secure **by design**


## Azure Active Directory
- Cloud based identity and access management sevice
- Database for the purpose of authentication
- Single sign on

## Conditional access
- e.g. if our user Bob is trying to access the app from an unauthorised netowrk, do not allow.
- It allows more than if Bob==Bob.

## Resource Locks
- Protect your Azure resources from accidental deletion/modification
- You chave to unlock it to delete it

## Tags
- Provides metadata for your Azure Resources
- Consists of a name:value pair
- e.g. owner:joe, department:marketing, environment:production
- VERY IMPORTANT TO USE !

## Azure Policy
- Evaluates and identifies Azure resources that do not comply with your policies
- e.g. if anyone in the organisation is building a VM, it cannot be bigger than a certain size

## Azure pricing and lifecycle
- Costs vary depending on resource type, servive, location, bandwidth, reserved instances, azure hybrid use benefit
- Use Azure Pricing Calculator to see how much stg will cost
- Monitor usage to minimise cost
- Free features do not offer SLAs


