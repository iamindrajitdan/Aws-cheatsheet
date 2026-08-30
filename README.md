# Cloud Computing

Service delivery model over the internet (cloud). This includes but is not limited to:
* **Compute power:** Servers such as Windows, Linux, hosting environments, etc.
* **Storage:** Files and/or databases.
* **Networking:** In Azure, but also outside when connecting to your company network.
* **Analytics services:** For visualization and telemetry data.

## Key Concepts
* **Scalability:** The ability to scale (allocate and deallocate resources at any time).
* **Elasticity:** The ability to scale dynamically.
* **Agility:** The ability to react fast (scale quickly).
* **Fault tolerance:** The ability to maintain system uptime while physical and service component failures happen.
* **Disaster recovery:** The process and design principle which allows a system to recover from natural or human-induced disasters.
* **High availability:** The agreed level of operational uptime for the system. It is a simple calculation of system uptime versus the whole lifetime of the system. 
  * `Availability = uptime / (uptime + downtime)`

## Economies of Scale
The principle of economies of scale states that as companies grow, they become more effective at managing shared operations. Be that HR and hiring, taxes, accounting, internal operations, marketing, big purchases via contracts meaning better discounts, etc.

Because of those, companies can save/earn more which in return allows for a reduction in the cost of their services to their customers. This is the so-called ‘price per unit’. 

It’s not possible to go to 0 because, in the end, some underlying infrastructure needs to run to provide the services. But the larger the scale, the more benefits can be passed to customers. In fact, at the current scale, Microsoft can already offer multiple services for free due to how small a fraction of the cost it is for them.

## CapEx vs OpEx
Differences between Capital Expenditure and Operational Expenditure:

| Feature | Capital Expenditure (CapEx) | Operational Expenditure (OpEx) |
|---|---|---|
| **Up front cost** | Significant | None |
| **Ongoing cost** | Low | Based on usage |
| **Tax Deduction** | Over time | Same year |
| **Early Termination** | No | Anytime |
| **Maintenance** | Significant | Low |
| **Value over time** | Lowers | No change |

## What is a Consumption-Based Model?
The consumption-based model is a pricing model used in the cloud so that customers are only charged based on their resource usage.

This model is characterized by:
* No associated upfront cost.
* No wasted resources, as no charges are incurred for unused resources. *(Note: "Unused" is different per service. For instance, blob storage that stores any data is considered used as it consumes space. VMs that are running consume CPU/memory even without traffic, so they incur charges).*
* Pay for what you need.
* Stop paying when you don’t.

Consumption is the virtual metric used to calculate how much each resource (service) in Azure was used. Each service has many smaller metrics that track its consumption to offer the best possible pricing model on a very granular level.

---

## Service Models Responsibilities
"As a service" means which party will manage the particular layer and all the layers below.

* **Software layer:** Consists of the application (code and set) & the application data.
* **Platform layer:** Means all the supporting software and the operating system required to host the application.
* **Infrastructure layer:** Consists of the hardware, infrastructure, and virtualization required to host the platform.

| Component | Layer |
|---|---|
| Application | Software |
| Data | Software |
| Runtime | Platform |
| Middleware | Platform |
| Operating System | Platform |
| Virtualization | Infrastructure |
| Servers | Infrastructure |
| Networking | Infrastructure |
| Storage | Infrastructure |

### Responsibility Matrix

| Layer | On-Premises | IaaS | PaaS | SaaS |
|---|---|---|---|---|
| **Application** | You | You | You | Cloud provider |
| **Data** | You | You | You | Cloud provider |
| **Runtime** | You | You | Cloud provider | Cloud provider |
| **Middleware** | You | You | Cloud provider | Cloud provider |
| **Operating System** | You | You | Cloud provider | Cloud provider |
| **Virtualization** | You | Cloud provider | Cloud provider | Cloud provider |
| **Servers** | You | Cloud provider | Cloud provider | Cloud provider |
| **Networking** | You | Cloud provider | Cloud provider | Cloud provider |
| **Storage** | You | Cloud provider | Cloud provider | Cloud provider |

---

## Cloud Deployment Model
Cloud Deployment Model is simply a separation which describes where the company resources are deployed (whether in a public cloud provider environment or private datacenter).

| Model | Cloud Provider | Own Datacenter |
|---|---|---|
| **Public** | ✅ | ✖ |
| **Hybrid** | ✅ | ✅ |
| **Private** | ✖ | ✅ |

### Public Cloud
* **Key Characteristics:** Everything runs on cloud provider hardware. No local hardware. Some services share hardware with other customers.
* **Advantages:** No CapEx (No initial investment), High Availability, Agility, Pay as you Go (PAYG) pricing, No hardware maintenance, No deep technical skills required.
* **Disadvantages:** Not all security and compliance policies can be met, No ownership over the physical infrastructure, Rare specific scenarios can’t be done.

### Private Cloud
* **Key Characteristics:** Everything runs on your own datacenter. Self-service should be provided. You maintain the hardware.
* **Advantages:** Can support any scenario, Total control over security and infrastructure, Can meet any security and compliance policy.
* **Disadvantages:** Initial investment is required (CapEx), Limited agility constrained by server capacity and team skills, Very dependent on IT skills & expertise.

### Hybrid Cloud
* **Key Characteristics:** Combines both Public & Private cloud.
* **Advantages:** Great flexibility, You can run any legacy apps in private cloud, Can utilize existing infrastructure, Meet any security & compliance requirements, Can take advantage of all public cloud benefits.
* **Disadvantages:** Can be more expensive, Complicated to manage due to larger landscape, Most dependent on IT skills & expertise from all three models.

---

## Azure Core Infrastructure

### Data Center
* Physical facility.
* Hosting for a group of networked servers.
* Own power, cooling & networking infrastructure.

### Region
* Geographical area on the planet.
* One, but usually more, datacenters connected with a low-latency network (<2 milliseconds).
* Location for your services.
* Some services are available only in certain regions, while some are global services (not assigned/deployed in a specific region).
* Globally available with 50+ regions.
* Special government regions (US DoD Central, US Gov Virginia, etc.).
* Special partnered regions (China East, China North).

### Availability Zone
* Regional feature.
* Grouping of physically separate facilities designed to protect from data center failures.
* If a zone goes down, others continue working.
* **Two service categories:**
  * Zonal services (Virtual Machines, Disks, etc.)
  * Zone-redundant services (SQL, Storage, etc.)
* Not all regions are supported (supported regions have three or more zones).
* A zone is one or more data centers.

### Region Pair
* Each region is paired with another region, making it a region pair.
* Region pairs are static and cannot be chosen.
* Each pair resides within the same geography (Exception: Brazil South).
* Physical isolation with at least 300 miles distance (when possible).
* Some services have platform-provided replication.
* Planned updates roll out sequentially across pairs.
* Data residency is maintained for disaster recovery.

| Region Pair A | Region Pair B |
|---|---|
| East US | West US |
| UK West | UK South |
| North Europe (Ireland) | West Europe (Netherlands) |
| East Asia (Hong Kong) | Southeast Asia (Singapore) |

### Geographies
* Discrete market typically containing two or more regions.
* Ensures data residency, sovereignty, resiliency, and compliance requirements are met.
* Fault-tolerant to protect from region-wide failures.
* Broken up into areas: Americas, Europe, Asia Pacific, Middle East and Africa.
* Each region belongs to only one Geography.

---

## Azure Management

### Azure Resource
* Object used to manage services in Azure.
* Represents service lifecycle.
* Saved as a JSON definition.

### Resource Groups
* Grouping of resources that holds logically related resources.
* Typically organized by: Type, Lifecycle (app, environment), Department, Billing, Location, or a combination of those.
* **Additional Info:**
  * Each resource must be in one, and only one, resource group.
  * Resource groups have their own location assigned, but resources inside them can reside in different locations.
  * Resources can be moved between resource groups.
  * Resource groups can’t be nested.
  * Organize based on organization needs, considering: Billing, Security and access management, Application Lifecycle.

### Resource Manager (ARM)
* Management Layer for all resources and resource groups.
* Unified language.
* Controls access and resources.

---

## Compute & Virtualization

### Virtualization
* Emulation of physical machines.
* Different virtual hardware configuration per machine/app.
* Different operating systems per machine/app.
* Total separation of environments (file systems, services, ports, middleware, configuration).

### Virtual Machines (VMs)
* **IaaS (Infrastructure as a Service)**
* Total control over the operating system and the software.
* Supports marketplace and custom images.
* **Best suited for:** Custom software requiring custom system configuration, Lift-and-shift scenarios, Running any application/scenario (web apps, databases, desktop apps, jumpboxes, gateways, etc.).

### Virtual Machine Scale Sets
* **IaaS**
* Set of identical virtual machines with built-in auto-scaling features.
* Designed for manual and auto-scaled workloads like web services, batch processing, etc.

### Containers
* Use host’s operating system to emulate the OS (whereas VMs emulate hardware).
* Lightweight (no O/S overhead).
* Lower development effort and maintenance.
* Quicker response to demand changes.

### Azure Container Instances (ACI)
* **PaaS**
* Simplest and fastest way to run a container in Azure (Serverless Containers).
* Designed for small/simple web apps/services, background jobs, and scheduled scripts.

### Azure Kubernetes Service (AKS)
* **PaaS**
* Open-source container orchestration platform.
* Highly scalable and customizable.
* Designed for high-scale container deployments.

### App Service
* **PaaS**
* Designed as an enterprise-grade web application service.
* Supports multiple programming languages and containers.

### Azure Functions (Function Apps)
* **PaaS / FaaS (Serverless)**
* Two hosting/pricing models: Consumption-based plan and Dedicated plan.
* Designed for micro/nano-services.

#### Compute Summary
* **Virtual Machines (IaaS):** Custom software/requirements, high control.
* **VM Scale Sets (IaaS):** Auto-scaled VM workloads.
* **Container Instances (PaaS):** Simple container hosting, easy to start.
* **Kubernetes Service (PaaS):** Highly scalable container platform.
* **App Services (PaaS):** Web applications with enterprise hosting features.
* **Functions (Serverless):** Micro/nano-services, consumption-based pricing.

---

## Azure Networking
Connects cloud and on-premises networks and provides internal cloud routing.

* **Azure Virtual Network (VNet):** Logically isolated networking components. Segmented into one or more discrete sections (subnets). Enables communication of resources with each other, internet, and on-premises. Scoped to a single region (VNet peering allows cross-region). Handles Isolation, Segmentation, Communication, Filtering, Routing.
* **Azure Load Balancer:** Even traffic distribution. Supports inbound/outbound, high-availability, TCP/UDP, internal/external traffic, and port forwarding. High scale.
* **VPN Gateway:** Specific type of virtual network gateway for on-premises to Azure traffic over the public internet.
* **Application Gateway:** Web traffic load balancer, Web application firewall, Redirection, Session affinity, URL Routing, SSL termination.
* **Content Delivery Network (CDN):** Defines content, minimizes latency via POPs (points of presence) across many locations.

---

## Data & Storage

### Data Types
* **Structured:** Data represented using tables with strict schemas. Used in relational databases.
* **Semi-structured:** Data represented using tables but without a strict defined schema (NoSQL). Rows must only have a unique key identifier.
* **Unstructured:** Any files in any format (binary files, images, movies, etc.).

### Storage Account
A group of services used to store files, messages, and semi-structured data. Highly scalable (petabytes), highly durable (up to 16 nines), and the cheapest per GB storage.
* **Blob Storage:** Binary Large Object. Designed for unstructured files. Three tiers: Hot (frequent access), Cool (infrequent access), Archive (rarely accessed).
* **Queue Storage:** Storage for small pieces of data (messages). Designed for scalable asynchronous processing.
* **Table Storage:** Storage for semi-structured data (NoSQL). Fast access, no strict schema or foreign keys.
* **File Storage:** Storage for files accessed via shared drive protocols (SMB). Designed to extend on-premise file shares (lift-and-shift).
* **Disk Storage:** Persistent storage for VMs. Comes in different sizes, types (SSD, HDD), and performance tiers. Disks can be unmanaged or managed.

### Databases
* **Cosmos DB:** Globally distributed NoSQL (semi-structured) database service. Schema-less. Multiple APIs (SQL, MongoDB, Cassandra, Gremlin, Table Storage). Designed for highly responsive, low-latency (<10ms) multi-regional applications.
* **SQL Database:** Relational database service (PaaS / DBaaS). Structured data with rich query capabilities.
  * *Azure SQL product family:* Azure SQL Database, Azure Database for MySQL, Azure Database for PostgreSQL, Azure SQL Managed Instance, Azure SQL on VM (IaaS), Azure Synapse Analytics (formerly SQL DW).

---

## Azure Marketplace
An “Azure Shop” where you purchase services and solutions for the Azure platform. Products are templates delivered by first and third-party vendors and can leverage IaaS, PaaS, and SaaS categories.

---

## Internet of Things (IoT)
A network of internet-connected devices embedded in everyday objects enabling sending and receiving data (settings and telemetry).
* **Azure IoT Hub:** PaaS. Managed service for bi-directional communication. Highly secure/scalable. Supports HTTPS, AMQP, MQTT.
* **Azure IoT Central:** SaaS. IoT App Platform with industry-specific templates. Requires no deep technical knowledge. Built on top of IoT Hub.
* **Azure Sphere:** Secure end-to-end IoT solution. Includes certified MCU chips, Azure Sphere OS (Linux-based), and Azure Security Service for trusted device-to-cloud communication.

---

## Big Data & Analytics
Technology that extracts, processes, and analyzes information too large/complex for traditional software. Characterized by the 3 V's: Velocity, Volume, and Variety.
* **Azure Synapse Analytics:** PaaS big data platform (formerly SQL DW). Includes Spark, Synapse SQL (dedicated and on-demand pools), and Synapse Pipelines (Data Factory ETL).
* **Azure HDInsight:** PaaS multi-purpose big data platform supporting Hadoop, Spark, Kafka, HBase, Hive, Storm.
* **Azure Databricks:** PaaS big data collaboration platform based on Apache Spark. Unified workspace for notebooks, clusters, and data.

---

## Artificial Intelligence & Machine Learning
AI is the simulation of human intelligence by software. Machine Learning is a subcategory where software is “taught” to draw conclusions and make predictions from data.
* **Azure Machine Learning:** PaaS for creating, managing, and publishing ML models.
  * *Features:* Notebooks (Python/R), Automated ML, Designer (no-code graphical interface), Data & Compute management, Pipelines for orchestrating tasks.

---

## Serverless & Integration
Cloud-hosted execution environments that abstract the underlying infrastructure.
* **Azure Functions:** FaaS. For nano-services and event-based applications. Scales quickly.
* **Azure Logic Apps:** PaaS. Serverless enterprise integration service. 200+ connectors. No-code orchestration of business processes and workflows.
* **Azure Event Grid:** Fully managed event routing service using a publish-subscribe model. Designed for near-real-time applications.

---

## DevOps
Practices that combine development (Dev) and operations (Ops) to shorten the lifecycle and provide CI/CD capabilities.
* **Azure DevOps:** Collection of services including Boards (tracking), Pipelines (CI/CD workflows), Repos (Git versioning), Test Plans, and Artifacts. Extensible via Marketplace.
* **Azure DevTest Labs:** PaaS for creating sandbox environments for developers/testers. Quick setup of self-managed VMs with policies (quotas, auto-shutdowns).

---

## Management Tools
* **Azure Portal:** Public web-based interface.
* **Azure PowerShell:** Automation CLI tool. 
  * Examples: `Connect-AzAccount`, `Get-AzResourceGroup`, `New-AzResourceGroup`, `New-AzVm`.
* **Azure CLI:** Python-based command line interface.
  * Examples: `az login`, `az group list`, `az group create`, `az vm create`.
* **Azure Cloud Shell:** Browser-based scripting environment supporting both PowerShell and CLI. Free and integrated into the Azure Portal, VS Code, and Windows Terminal.
* **Azure Mobile App:** Management on the go.
* **Azure Advisor:** Free personalized consultant service providing recommendations for Cost, Security, Reliability, Performance, and Operational Excellence.

---

## Security & Networking Security

* **Network Security Groups (NSG):** Filters inbound/outbound traffic to Azure resources in a VNet. Controlled by rules specifying Source/Destination, Protocol, Port (e.g., 3389 RDP, 22 SSH, 80 HTTP), Direction, and Priority.
* **Application Security Groups (ASG):** Groups VMs to reduce maintenance effort (assign rules to the ASG instead of explicit IP addresses).
* **User-defined Routes (UDRs):** Custom static routes via Azure Route Table to override default Azure routing.
* **Azure Firewall:** PaaS managed firewall. High availability, scalable, supports FQDN filtering, integrated with Azure Monitor.
* **Azure DDoS Protection:** Protects against Distributed Denial of Service attacks.
  * *Basic:* Automatically enabled for all Azure platform.
  * *Standard:* Additional mitigation, monitoring, and machine-learning traffic analysis for VNet resources.

### Identity & Access Management
* **Authentication:** Verification of identity.
* **Authorization:** Ensuring the identity has permissions to access the resource.
* **Azure Active Directory (Azure AD):** Identity and Access Management service. Manages users, groups, and applications. Used by Azure, Microsoft 365, Live.com, etc.
* **Multi-factor Authentication (MFA):** Proving identity using more than one factor (Knowledge, Possession, Physical Characteristic, Location).

### Azure Security Center / Microsoft Defender
* **Free Tier:** Continuous assessments, security score, basic recommendations.
* **Paid Tier (Azure Defender ON):** Hybrid security, threat protection, vulnerability scanning, Just-in-Time (JIT) VM access.

### Azure Key Vault
* PaaS secure storage for Keys, Secrets, and Certificates. Provides centralization and access monitoring.

---

## Governance & Compliance

### Role-Based Access Control (RBAC)
Fine-grained access management built on Azure Resource Manager (ARM).
* **Role:** What can be done? (Collection of actions/permissions).
* **Security Principal:** Who can do it? (User, group, service principal, managed identity).
* **Scope:** Where can it be done? (Management Group > Subscription > Resource Group > Resource).
* **Role Assignment:** The combination of Role + Principal + Scope.

### Azure Resource Locks
Prevents accidental deletion/modification. Overrides RBAC permissions.
* **ReadOnly:** Only read actions allowed.
* **CanNotDelete:** All actions allowed except delete.
* Inherited hierarchically. Management Groups cannot be locked.

### Azure Resource Tags
Name/Value pairs used to logically organize resources for billing, security, and automation (e.g., `environment = production`). **Not** inherited by default.

### Azure Policy
Enforces resource governance, compliance, and cost management by focusing on resource *properties* (unlike RBAC which focuses on user *actions*). Can deny, audit, or modify resources. Checked during resource creation/update.
* **Initiative:** A group of policy definitions.

### Azure Blueprints
Centralized storage for organizationally approved design patterns. Packages Resource Groups, ARM Templates, Policy Assignments, and Role Assignments into a single reproducible package.

---

## Cloud Adoption Framework
A set of tools, best practices, and guidelines to help companies adopt the cloud.

1. **Strategy:** Understand motivation (WHY move?) and determine Business Outcomes (WHAT to measure?). Build a business justification (ROI) using TCO and Pricing Calculators. Pick a first POC project.
2. **Plan:** Inventory the Digital Estate. Choose one of the 5 R’s (Rehost, Refactor, Rearchitect, Rebuild, Replace). Align organization and skill readiness.
3. **Ready:** Use Azure Setup Guide and establish an Azure Landing Zone. Expand it and apply best practices.
4. **Adopt:** Migrate applications, verify scenarios, and improve processes.
5. **Innovate:** Build business value, use the Innovation Guide tools, and gather feedback.
6. **Govern & Manage:** Define governance solutions to address needs, provide agility, and control risk.
7. **Organize:** Define roles (e.g., RACI matrix).

---

## Compliance Documents & Sovereign Regions

| Document/Website | Info | Offers | Audience |
|---|---|---|---|
| **Microsoft Privacy Statement** | Collection, Purpose and Usage of Personal Data | All Microsoft offers | Everyone |
| **Online Services Terms (OST)** | Licensing Terms (legal agreement) & usage rights | Microsoft Online Services | Legal teams |
| **Data Protection Addendum** | Obligations regarding processing of customer data | Microsoft Online Services | Legal/Security teams |
| **Trust Center** | One-stop portal for security, compliance, privacy policies | Microsoft Online Services | Legal/Security teams, Admins |
| **Azure Compliance Documentation** | Focused specifically on Azure compliance offerings | Azure | Legal/Security teams, Admins |

### Azure Sovereign Regions
Provide Azure services in markets with very strict regulatory requirements. Physically isolated from standard regions.
* **Azure Government:** US government. Only authorized screened personnel get access.
* **Azure China:** Chinese market. Operated by Chinese telecom 21Vianet.

---

## Cost Management & SLAs

### Cost Affecting Factors & Savings
* **Base Cost:** Driven by Resource Types, Services, Location, and Bandwidth (outbound/egress costs money; inbound is free).
* **Azure Reservations:** Purchase compute for 1 or 3 years in advance for massive discounts.
* **Azure Spot VMs:** Purchase unused VM capacity at a discount (interruptible workloads).
* **Hybrid Use Benefit:** Bring your existing Windows Server or SQL Server licenses to the cloud.

### Cost Tools
* **Pricing Calculator:** Estimate future costs of Azure services.
* **TCO Calculator:** Compare the cost of running workloads on-premise vs. Azure.
* **Azure Cost Management:** Centralized reporting, budgets, alerts, and cost recommendations.

### Service Level Agreement (SLA)
A formal agreement (a promise) between Microsoft and the customer regarding service availability/uptime. Breaking the SLA results in a Service Credit (discount). Free and Preview services typically have 0% SLA.

| SLA | Monthly Downtime |
|---|---|
| 99% | 7h 18m 17s |
| 99.5% | 3h 39m 8s |
| 99.9% | 43m 49s |
| 99.95% | 21m 54s |
| 99.99% | 4m 22s |
| 99.999% | 26s |

**Composite SLA Formulas:**
* **Logical AND (Adding Dependency):**
  ```text
  Availability = Availability(S1) * Availability(S2)
  Example: 99.95% * 99.95% = ~99.9%
