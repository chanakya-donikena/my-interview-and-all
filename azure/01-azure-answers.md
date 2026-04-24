# DevOps Engineer (Azure) – Interview Questions & Answers

**Experience Level: 4 Years**

---

## ☁️ Azure Fundamentals

**What is Microsoft Azure?**
Microsoft Azure is a cloud computing platform that provides services like compute, storage, networking, databases, and DevOps tools to build, deploy, and manage applications globally.

**Regions vs Availability Zones vs Availability Sets**

* Region: Geographic area containing datacenters
* Availability Zone: Physically separate datacenters within a region
* Availability Set: Logical grouping of VMs to ensure fault tolerance

**Resource Groups**
Logical containers to group related resources for easier management and deployment.

**App Service vs VM vs AKS**

* App Service: Platform as a Service for web apps
* VM: Infrastructure as a Service with full control
* AKS: Managed Kubernetes for container orchestration

**Virtual Network (VNet)**
Private network in Azure for secure communication between resources.

---

## 🚀 CI/CD & DevOps

**CI/CD**
CI automates build and testing. CD automates deployment.

**Azure DevOps**
Provides repositories, pipelines, boards, and artifacts for complete DevOps lifecycle.

**Azure Pipelines vs GitHub Actions**

* Pipelines: Enterprise-ready, advanced workflows
* GitHub Actions: Lightweight, GitHub-integrated

**Multi-stage Pipelines**
Separate stages like build, test, deploy with approvals.

**Artifacts**
Outputs like binaries or container images used for deployment.

**Scenario: Pipeline Design**
Code → Build → Test → Docker Image → Push → Deploy to staging → Approval → Production.

---

## 🐳 Containers & Kubernetes

**Docker**
Used to containerize applications with dependencies.

**Kubernetes Architecture**
Master components manage cluster; worker nodes run applications.

**AKS**
Managed Kubernetes service in Azure.

**Deployment Management**
Using YAML manifests, Helm charts, rolling updates.

**ReplicaSet vs Deployment vs StatefulSet**

* ReplicaSet: Maintains pod count
* Deployment: Manages updates and rollback
* StatefulSet: Used for stateful apps

**CrashLoopBackOff Troubleshooting**
Check logs, configuration, environment variables, and resource limits.

---

## 🏗️ Infrastructure as Code

**IaC**
Managing infrastructure using code.

**ARM vs Terraform**

* ARM: Azure-native
* Terraform: Multi-cloud

**Terraform State**
Stores infrastructure state.

**Secrets Management**
Use secure storage like Key Vault.

**Bicep**
Simplified language for ARM templates.

---

## 🔐 Security

**Azure Active Directory**
Manages identity and access.

**Service Principal vs Managed Identity**

* SP: Manual setup
* Managed Identity: Auto-managed

**RBAC**
Controls access via roles.

**Key Vault**
Stores secrets securely.

**NSG**
Controls inbound and outbound traffic.

---

## 📊 Monitoring

**Azure Monitor**
Collects logs and metrics.

**Log Analytics vs App Insights**

* Log Analytics: Query logs
* App Insights: App performance

**Alerts**
Triggered based on metrics/logs.

**KQL**
Query language for logs.

---

## 🌐 Networking

**Load Balancer vs App Gateway**

* Load Balancer: Layer 4
* App Gateway: Layer 7

**Azure DNS**
Manages domain resolution.

**VPN vs ExpressRoute**

* VPN: Internet-based
* ExpressRoute: Private connection

**VNet Peering**
Connects virtual networks.

---

## ⚙️ Scripting

**Languages**
Bash, PowerShell, Python.

**Automation Tasks**
Deploy resources, clean unused services.

**CLI vs PowerShell**
CLI is cross-platform; PowerShell is object-based.

---

## 🔄 Version Control

**Git**
Tracks code changes.

**Branching Strategies**
GitFlow and trunk-based development.

**Merge Conflicts**
Resolve manually and test.

---

## ⚡ Performance

**Cost Optimization**
Use reserved instances, autoscaling, and remove unused resources.

**Auto-scaling**
Automatically adjusts resources.

**Scaling Types**
Horizontal (add instances), Vertical (increase size).

---

## 🧠 Scenario-Based

**Deployment Failure**
Check logs, debug pipeline, rollback if needed.

**Zero Downtime Deployment**
Use blue-green or rolling deployment.

**Cost Reduction**
Right-size resources and use spot instances.

**High Availability**
Use zones, load balancers, redundancy.

**Secrets in CI/CD**
Use secure vault integration.

---

## 🎯 Behavioral

**Project Explanation**
Explain architecture, tools, and CI/CD flow.

**Challenges**
Describe problem, solution, and outcome.

**Collaboration**
Agile process and teamwork.

**Production Issue**
Explain root cause and prevention.

---

## Tips for Interviews

* Give real-world examples
* Focus on problem-solving
* Highlight tools like AKS, Terraform, CI/CD
* Be clear and structured in answers

---

