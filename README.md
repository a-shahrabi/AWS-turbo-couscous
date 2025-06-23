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


| Feature        | Description              |
| -------------- | ------------------------ |
| EC2            | Scalable virtual servers |
| AMI            | Template for instances   |
| EBS            | Persistent block storage |
| Security Group | Virtual firewall         |
| Key Pair       | SSH credentials          |
| ELB            | Load balancing           |
| Auto Scaling   | Adjust instance count    |
| IAM Role       | Grant permissions to EC2 |
| VPC/Subnet     | Networking setup         |
| CloudWatch     | Monitoring & alerts      |




S3 Storage Classes: 


Standard - Frequently accessed, highest cost, 99.999999999% (11 9's) durability
Standard-IA - Infrequent access, 30-day minimum, retrieval fees
One Zone-IA - Single AZ, 20% cheaper than Standard-IA, less availability
Intelligent-Tiering - Automatically moves objects between tiers based on access
Glacier Instant Retrieval - Archive with millisecond access, 90-day minimum
Glacier Flexible Retrieval - 1-12 hours retrieval, 90-day minimum
Glacier Deep Archive - Cheapest, 12-48 hours retrieval, 180-day minimum

Lifecycle Policies
Automatically transition objects between storage classes:


Versioning (You enabled this!)

Keeps multiple versions of objects
Protects against accidental deletion
Previous versions can be in different storage classes
Delete markers for "deleted" objects

Security & Access Control

Bucket Policies - JSON policies attached to buckets
ACLs - Legacy permissions (AWS recommends bucket policies)
Block Public Access - Safety net to prevent accidental exposure
Pre-signed URLs - Temporary access to private objects

Advanced Features

Cross-Region Replication (CRR) - Copy objects to different regions
Same-Region Replication (SRR) - Copy within same region
Transfer Acceleration - Use CloudFront edge locations for faster uploads
Multipart Upload - Upload large files in pieces
S3 Select - Query data without downloading entire object
