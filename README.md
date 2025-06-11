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
