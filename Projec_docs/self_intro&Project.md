### **Self-Introduction with Project Details (DevOps Engineer – Gopi Krishna Yakkati)**  

**Hello, my name is Gopi Krishna Yakkati, and I am a DevOps Engineer with 5 years of experience in cloud services, automation, and CI/CD pipeline management.**  

I have expertise in **AWS and Azure**, focusing on **infrastructure as code (IaC) using Terraform**, **containerization with Docker and Kubernetes**, and **automation with Ansible**. My experience includes designing, implementing, and managing **CI/CD pipelines** using Jenkins and Azure DevOps, ensuring seamless and automated deployments.  

I specialize in **cloud security, monitoring, and vulnerability scanning**, integrating tools like **SonarCloud, Trivy, Prometheus, and Grafana** to enhance application reliability and security. Additionally, I have experience working with **AWS Auto Scaling, Load Balancers, and security group configurations** to optimize cloud infrastructure.  

Currently based in **Bangalore, India**, I hold a **B.Tech in Electrical and Electronics Engineering (2018)** and am passionate about streamlining DevOps workflows, improving automation, and ensuring high availability of applications.  

---

## **Project 1: Internal Application Deployment on AWS (Microservices Architecture)**  
### **Project Overview:**  
The project involved deploying an internal web-based application used by employees for project management. The goal was to migrate from a monolithic architecture to **microservices**, ensuring **scalability, high availability, and automated deployments**.  

### **Key Responsibilities & Technologies Used:**  
- **Infrastructure as Code (IaC):** Used **Terraform** to provision AWS resources like **VPC, EC2, RDS, ALB, Auto Scaling Groups, and Security Groups**.  
- **Containerization & Orchestration:** Deployed the application as **Docker containers** and orchestrated them using **Kubernetes (EKS)**.  
- **CI/CD Implementation:** Designed a **Jenkins pipeline** for automating build, test, and deployment processes.  
- **Security & Compliance:** Integrated **Trivy** for scanning Docker images and **SonarCloud** for code quality checks.  
- **Monitoring & Logging:** Used **Prometheus and Grafana** for performance monitoring and **ELK Stack** for centralized logging.  

### **Outcome:**  
- Reduced deployment time by **60%** with automated CI/CD pipelines.  
- Improved system availability with **AWS Auto Scaling and Load Balancer** integration.  
- Strengthened security by implementing **IAM roles, Security Groups, and vulnerability scanning**.  

---

## **Project 2: Azure Kubernetes Service (AKS) Setup for Internal CRM**  
### **Project Overview:**  
This project aimed to modernize an internal **Customer Relationship Management (CRM) application** by migrating it from on-premises servers to **Azure Kubernetes Service (AKS)** for improved scalability and performance.  

### **Key Responsibilities & Technologies Used:**  
- **Terraform Automation:** Defined **AKS cluster, Virtual Networks, Azure Storage, and Role-Based Access Control (RBAC)** using **Terraform modules**.  
- **CI/CD Implementation:** Configured **Azure DevOps pipelines** to automate the build, test, and deployment process for microservices.  
- **Application Deployment:** Deployed **containerized CRM services** on AKS and managed rolling updates with **Helm charts**.  
- **Security Best Practices:** Implemented **Azure Key Vault** for managing application secrets and **Azure Security Center** for vulnerability management.  
- **Monitoring & Alerts:** Integrated **Azure Monitor, Prometheus, and Grafana** to track application performance and send alerts for anomalies.  

### **Outcome:**  
- Achieved **99.9% application uptime** with Kubernetes auto-healing and horizontal scaling.  
- Reduced operational overhead by **50%** through **fully automated deployments**.  
- Enhanced security posture with **RBAC, Azure Key Vault, and Kubernetes Network Policies**.  

---
## **Project 1: Microservices-Based Internal Web Application Deployment on AWS**  

### **Project Overview:**  
This project involved deploying an **internal web application** with a **microservices architecture** on AWS. The goal was to ensure **scalability, high availability, and automation** while maintaining security and compliance.  

### **Architecture & Technologies Used:**  
- **Cloud Platform:** AWS  
- **Container Orchestration:** AWS Elastic Kubernetes Service (EKS)  
- **Infrastructure as Code (IaC):** Terraform  
- **CI/CD Automation:** Jenkins  
- **Security:** AWS IAM, Security Groups, AWS WAF  
- **Monitoring & Logging:** Prometheus, Grafana, AWS CloudWatch  

### **Microservices Architecture & Workloads:**  
The application was broken into multiple **Docker containerized microservices** and deployed on **AWS EKS**.  

| Microservice         | Replicas | CPU Allocation | Memory Allocation |
|----------------------|---------|---------------|-------------------|
| **User Service**     | 2       | 500m CPU      | 512MB RAM        |
| **Product Service**  | 3       | 700m CPU      | 1GB RAM          |
| **Order Service**    | 3       | 800m CPU      | 1.5GB RAM        |
| **Notification Service** | 2    | 400m CPU      | 512MB RAM        |
| **Gateway Service**  | 2       | 500m CPU      | 512MB RAM        |

### **Kubernetes Cluster Sizing & Configuration:**  
- **Cluster Type:** AWS EKS  
- **Master Nodes:** Managed by AWS  
- **Worker Nodes:** 3 EC2 instances (`m5.large`, 2 vCPUs, 8GB RAM)  
- **Total Cluster Capacity:** 6 vCPUs, 24GB RAM  
- **Auto Scaling:** Min 2 nodes, Max 5 nodes  

### **Key Responsibilities & Implementation:**  
- **Infrastructure Automation:**  
  - Used **Terraform** to provision AWS resources: **VPC, EKS, ALB, IAM roles, Security Groups**.  
- **CI/CD Implementation:**  
  - Configured **Jenkins pipelines** to automate **Docker image builds, testing, and deployments**.  
- **Security & Compliance:**  
  - Configured **IAM roles, VPC security groups, AWS WAF, and encrypted secrets management**.  
- **Monitoring & Logging:**  
  - Integrated **Prometheus, Grafana, and AWS CloudWatch** for centralized monitoring.  

### **Outcome & Benefits:**  
✅ Reduced deployment time by **70%** with automated CI/CD pipelines.  
✅ Improved **scalability** with Kubernetes **Horizontal Pod Autoscaler (HPA)**.  
✅ Strengthened **security** by implementing **IAM roles, security groups, and AWS WAF**.  

---

## **Project 2: Azure Kubernetes Service (AKS) for Internal CRM Application**  

### **Project Overview:**  
This project involved deploying an **internal CRM (Customer Relationship Management) application** on **Azure Kubernetes Service (AKS)** to improve **scalability, security, and automation**.  

### **Architecture & Technologies Used:**  
- **Cloud Platform:** Azure  
- **Container Orchestration:** Azure Kubernetes Service (AKS)  
- **Infrastructure as Code (IaC):** Terraform  
- **CI/CD Automation:** Azure DevOps  
- **Security:** Azure Key Vault, RBAC, Kubernetes Network Policies  
- **Monitoring & Logging:** Azure Monitor, Prometheus, Grafana  

### **Microservices Architecture & Workloads:**  
The CRM application was built using **microservices architecture**, each deployed in **Azure AKS**.  

| Microservice         | Replicas | CPU Allocation | Memory Allocation |
|----------------------|---------|---------------|-------------------|
| **Auth Service**     | 2       | 700m CPU      | 1GB RAM          |
| **Customer Service** | 3       | 1 vCPU        | 2GB RAM          |
| **Billing Service**  | 3       | 1 vCPU        | 2GB RAM          |
| **Email Service**    | 2       | 500m CPU      | 512MB RAM        |
| **API Gateway**      | 2       | 800m CPU      | 1.5GB RAM        |

### **Kubernetes Cluster Sizing & Configuration:**  
- **Cluster Type:** Azure AKS  
- **Worker Nodes:** 4 Virtual Machines (`Standard_D4s_v3`, 4 vCPUs, 16GB RAM)  
- **Total Cluster Capacity:** 16 vCPUs, 64GB RAM  
- **Auto Scaling:** Min 3 nodes, Max 6 nodes  

### **Key Responsibilities & Implementation:**  
- **Infrastructure Automation:**  
  - Used **Terraform** to create **AKS cluster, Virtual Networks, Azure Load Balancer**.  
- **CI/CD Implementation:**  
  - Configured **Azure DevOps pipelines** to automate **Docker builds, testing, and deployments**.  
- **Security & Compliance:**  
  - Integrated **Azure Key Vault for secret management** and **RBAC for access control**.  
- **Monitoring & Logging:**  
  - Implemented **Azure Monitor, Prometheus, and Grafana** for real-time alerts and metrics.  

### **Outcome & Benefits:**  
✅ Achieved **99.9% uptime** with AKS **auto-scaling and self-healing**.  
✅ Reduced operational overhead by **50%** through **fully automated CI/CD pipelines**.  
✅ Improved **security compliance** with **RBAC and Azure Key Vault integration**.  

---

