# AWS Solutions Architect Associate (SAA) Study Guide

## Having gpt on the side to ask questions
## Contents
- [Core Concepts](#core-concepts)
- [Compute Services](#compute-services)
- [VPC & Networking](#vpc--networking)
- [IAM & Security](#iam--security)
- [Storage Services](#storage-services)
- [Other Services](#other-services)
- [Exam Tips](#exam-tips)

---

## 🎯 Core Concepts

### AWS Shared Responsibility Model
- **AWS Responsibility**: Physical infrastructure, host OS, network controls
- **Customer Responsibility**: Guest OS, application software, security groups, IAM, data encryption

### Service Categories
- **IaaS**: Infrastructure as a Service (EC2, VPC)
- **PaaS**: Platform as a Service (Elastic Beanstalk)
- **SaaS**: Software as a Service (WorkMail, WorkDocs)

---

## 💻 Compute Services

### EC2 (Elastic Compute Cloud)
**What it is**: Virtual servers in the cloud


Instance Types:
EC2 comes in different "flavors" optimized for different tasks:

General Purpose (t3, m5) - balanced CPU/memory, good for web servers
Compute Optimized (c5) - high-performance CPUs for intensive tasks
Memory Optimized (r5, x1) - lots of RAM for databases
Storage Optimized (i3) - fast local storage for data processing
GPU instances (p3, g4) - for machine learning, graphics

Internet → Route 53 (DNS) → CloudFront (CDN) → 
Application Load Balancer → Auto Scaling Group (EC2) → 
RDS Multi-AZ + ElastiCache → S3 (static files)

EC2 Fundamentals

Virtual servers in the cloud that you can configure and control
Pay only for what you use (by the second for Linux, by the hour for Windows)
Can scale up/down or in/out based on demand

Instance Types (Family + Size)

General Purpose: t3, t4g, m5, m6i (balanced CPU/memory)
Compute Optimized: c5, c6i (high-performance processors)
Memory Optimized: r5, r6i, x1e (high memory-to-CPU ratio)
Storage Optimized: i3, i4i, d3 (high sequential read/write)
Accelerated Computing: p3, p4, g4 (GPU instances)

| Family | Use Case                   |
| ------ | -------------------------- |
| t3/t4  | General Purpose            |
| c5/c6  | Compute-optimized          |
| m5/m6  | Balanced (General)         |
| r5/r6  | Memory-optimized           |
| p3/p4  | GPU for ML/AI              |
| i3     | Storage-optimized          |
| hpc6   | High performance computing |


| Option                      | Description                  | Use Case                            |
| --------------------------- | ---------------------------- | ----------------------------------- |
| **On-Demand**               | Pay per hour/second          | Short-term, unpredictable workloads |
| **Reserved**                | Commit 1-3 years             | Steady workloads, cost savings      |
| **Spot**                    | Bid on unused capacity       | Flexible workloads, big savings     |
| **Savings Plan**            | Flexible pricing model       | Discount for commitment             |
| **Dedicated Host/Instance** | Physical server for your use | Compliance, licensing needs         |

