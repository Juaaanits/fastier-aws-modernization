# AWS Solutions Architecture: Web Application Modernization

This repository contains the proposed architectural solution for **Fastier**, an online organization tool experiencing rapid growth. This project was completed as part of the **AWS APAC Solutions Architecture Virtual Experience Program (January 2026).**

---

## 📋 Project Overview

Fastier’s current **"all-in-one" architecture** on a single `t3.medium` EC2 instance has become a bottleneck. The goal of this project was to design a **scalable**, **highly available**, and **resilient architecture** to eliminate downtime, support linear growth, and implement a robust disaster recovery strategy.

### 🔧 Key Challenges Addressed

- **Performance:** Slow response times during peak traffic.
- **Reliability:** Server crashes due to memory exhaustion.
- **Availability:** No disaster recovery and downtime during deployments.
- **Scalability:** Manual scaling is no longer viable for their growth trajectory.

---

## 🏗️ Proposed Architecture

The new architecture transitions from a monolithic, single-server setup to a **decoupled, Multi-AZ (Availability Zone)** infrastructure.

### 1. Frontend & Content Delivery

- **Amazon S3:** Hosts the React SPA as a static website, offloading work from web servers.
- **Amazon CloudFront:** Caches content closer to users globally via a CDN, reducing latency.

### 2. Compute & Load Balancing

- **Application Load Balancer (ALB):** Distributes incoming traffic across multiple EC2 instances.
- **Auto Scaling Group (ASG):** Automatically adjusts the number of EC2 instances based on real-time CPU/memory usage.
- **Multi-AZ Deployment:** Instances are deployed across two Availability Zones to ensure uptime even in the event of a data center failure.

### 3. Database Management

- **Amazon RDS (PostgreSQL):** Managed database service.
- **Multi-AZ Replication:** Primary database in AZ 1 with synchronous standby in AZ 2 for instant failover and disaster recovery.

### 4. CI/CD & Automation

- **AWS CodePipeline:** Automates deployment processes, supporting **Rolling Updates** to prevent downtime during releases.

---

## 📧 Client Communication: Email Draft

```
To: Lilly.sawyer@fastier.com
From: [Your Name], AWS Solutions Architect
Subject: Scaling Fastier: Proposed AWS Architecture for High Availability

Hi Lilly,

Congratulations on Fastier's recent growth. I understand how frustrating performance bottlenecks and server crashes can be as you outgrow a single t3.medium instance. I've put together a new AWS design focused on scalability and high availability to address these issues.

How the new design helps:
- No more crashes: An Auto Scaling Group adds capacity during peaks and scales down to save costs.
- Faster response times: Amazon CloudFront caches your React frontend at edge locations closer to users.
- Zero downtime deployments: AWS CodePipeline supports rolling updates to keep the site available during releases.
- Disaster recovery: Amazon RDS Multi-AZ maintains a standby replica that takes over automatically during outages.

Understanding costs:
- Compute: Pay only for the number of EC2 instances running at any time.
- Storage/CDN: Billed based on data stored and served.
- Managed services: RDS and ALB have modest hourly fees that reduce downtime risk and maintenance overhead.

I've attached a high-level architecture diagram. I'd be happy to walk you through the transition plan - please let me know a good time for a call.

Best regards,
[Your Name]
Solutions Architect, AWS
```

---

## 🚀 How to View

- **Diagram:** Refer to `AWS Cloud Architecture.png` for the high-level architecture.
- **Tools Referenced:**  
  - AWS VPC  
  - EC2  
  - RDS  
  - S3  
  - Route 53  
  - CloudFront  
  - CodePipeline

---

## 🧪 Examples

*Note: This is an architecture design submission only. No code or infrastructure setup has been performed.*

---

## 👥 Contributors

- Juanito M. Ramos II – Aspiring AWS Solutions Architect

---

## 📄 License

This project is part of the **AWS APAC Solutions Architecture Virtual Experience Program**. 
