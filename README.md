# V-Profile Project: Multi-Tier Java Web Stack

Welcome to the **V-Profile Project**. This repository contains the configuration and automation scripts to set up a multi-tier social networking application locally. 

The goal of this project is to create a repeatable, automated local development environment (Local Lab) using **Infrastructure as Code (IaC)** principles.

---

##  Project Architecture

The application is a distributed system where multiple services work together to provide a seamless user experience.

![Project Architecture](images/Multi-Tier_Web_Stack_Automation.png)

### Service Stack:
* **Nginx**: Web Service & Load Balancer.
* **Apache Tomcat**: Java Application Server (Hosts the V-Profile Java app).
* **RabbitMQ**: Messaging Broker / Queuing Agent.
* **Memcached**: Database Caching Service.
* **MySQL**: Relational Database Management System.
* **Vagrant & VirtualBox**: For VM automation and management.

---

##  Automated Setup Workflow

Instead of manual installation, we use **Vagrant** to automate the creation and configuration of our Virtual Machines (VMs) on top of Oracle VM VirtualBox.

### Prerequisites
Before starting, ensure you have installed:
1.  **Oracle VM VirtualBox**: The hypervisor to run our VMs.
2.  **Vagrant**: The automation tool to provision the VMs.
3.  **Git Bash**: For executing commands and version control.

---

##  Step-by-Step Implementation

Follow these steps to get your local environment running:

### 1. Clone the Repository
```bash
git clone <project url>
cd Multi-Tier_Web_Stack_Automation
```

### 2. Provision the Infrastructure
Navigate to the vagrant directory and bring up the 5 Virtual Machines automatically:

Bash

```bash
cd vagrant
vagrant up
```

Note: This command reads the Vagrantfile and provisions the environment in VirtualBox.

### 3. Service Configuration Order
To ensure proper connectivity, services are configured in the following sequence:

- MySQL: Setup database and import schema.
- Memcached: Initialize the caching engine.
- RabbitMQ: Configure the message queuing agent.
- Tomcat: Build the Java application and deploy the .war file.
- Nginx: Configure the load balancer to point to the Tomcat instance.

### 4. Verification
Once the status is green, access the application by entering the Nginx IP address in your browser:

Plaintext

```text
http://<NGINX_VM_IP>
```

##  Repository Structure
- /vagrant: Contains the Vagrantfile (Infrastructure as Code).
- /src: Java application source code and Maven configurations.
- /scripts: Automated Shell scripts for middleware installation.

##  Key Learning Objectives
- IaC Mastery: Managed complex infrastructure via code rather than manual GUI clicks.
- System Interconnectivity: Implemented communication between Java apps, DBs, and Message Brokers.
- Troubleshooting: Developed skills in tracing errors across multi-tier distributed systems.
- Cloud Readiness: Established a baseline for future containerization (Docker) and orchestration (K8s).
- `/vagrant`: Vagrantfile + VM provisioning scripts
- `/src`: Java application source, Maven POM, and web resources
- `/scripts`: shell scripts for middleware installation and setup

##  Key Learning Objectives
- **IaC Mastery**: version-controlled infrastructure provisioning instead of manual GUI flows.
- **System Interconnectivity**: connecting relational DB, cache, message broker, app server, and load balancer.
- **Troubleshooting**: tracing cross-tier issues (DB, RabbitMQ, Tomcat, Nginx).
- **Cloud Readiness**: established a local baseline for Docker/K8s migration.

