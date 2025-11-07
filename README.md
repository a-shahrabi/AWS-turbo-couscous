# AWS Solutions Architect Associate (SAA) Notes:

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


**VPC Fundamentals**
- **Virtual Private Cloud** - Your own isolated network in AWS
- **CIDR Blocks** - Define IP address ranges (e.g., 10.0.0.0/16 = 65,536 IP addresses)
- **Region-specific** - Each VPC exists in one region but can span multiple AZs

**Core Components**

```
**1. Subnets**
- **Public Subnet** - Has route to Internet Gateway (can reach internet)
- **Private Subnet** - No direct internet access (more secure)
- **Each subnet exists in ONE Availability Zone**

**2. Route Tables**
- Control where network traffic goes
- Each subnet must be associated with a route table
- **0.0.0.0/0** means "all traffic" (default route)

**3. Internet Gateway (IGW)**
- Allows communication between VPC and internet
- One per VPC, highly available
- Required for public subnets

**4. NAT Gateway/Instance**
- Allows private subnets to reach internet (outbound only)
- **NAT Gateway** - Managed by AWS, highly available
- **NAT Instance** - EC2 instance you manage (legacy)

**Security Layers**

**5. Security Groups (Instance Level)**
- **Stateful** - if you allow inbound, response is automatically allowed outbound
- **Allow rules only** - cannot deny traffic
- Default: deny all inbound, allow all outbound

**6. Network ACLs (Subnet Level)**
- **Stateless** - must explicitly allow both inbound AND outbound
- **Allow and deny rules** - processed in order
- Default: allow all traffic

**Advanced Networking**
- **VPC Peering** - Connect two VPCs privately
- **Transit Gateway** - Central hub connecting multiple VPCs
- **VPC Endpoints** - Private connection to AWS services (no internet needed)

```

```
Design durable, secure, cost-optimized object storage with the right:

Access controls (block public, bucket policy, IAM, Access Points)

Data protection (encryption, versioning, Object Lock)

Lifecycle & storage class choices

Replication/DR patterns

Private access via VPC endpoints

Event integrations (S3→Lambda/SNS/SQS/EventBridge)

Performance & upload (multipart, Transfer Acceleration)

Durability: 11 nines (99.999999999%); region-scoped service; strong read-after-write consistency for PUT/DELETE and LIST.
```

```
Picker order: Image, Size, Network, Lock, Disk, Role, Script

Families: C M R G I T (Compute, Multi, RAM, GPU, IO, T-burst)

SG = Stateful; NACL = Numbered stateless

EBS persists; Instance Store disappears
```


### Amazon EC2: Comprehensive Beginner’s Guide for AWS Solutions Architect Associate (SAA) Exam
```
Introduction to Amazon EC2 (Elastic Compute Cloud)

Amazon Elastic Compute Cloud (EC2) is AWS’s core Infrastructure-as-a-Service (IaaS) offering that provides on-demand, resizable compute capacity in the cloud
docs.aws.amazon.com
. In simple terms, EC2 lets you launch virtual machines (called instances) on AWS’s global infrastructure. You have full control over the operating system and software on these instances, and you pay only for the compute time you use
aws.amazon.com
. EC2 is designed to easily scale up or down – you can quickly provision more servers during peak demand and shut them down when they’re no longer needed, enabling highly flexible “web-scale” computing
aws.amazon.com
. As part of the AWS ecosystem, EC2 often works alongside other services (for example, an application might run on EC2 but store data in Amazon S3 or use an AWS database service). This flexibility and integration make EC2 a fundamental building block in many cloud architectures.
```
```
Launching an EC2 instance involves choosing a machine image (AMI) as a template, selecting an instance type (virtual hardware profile), configuring networking (VPC, subnets, and assigning a security group firewall), and setting up access (key pairs for SSH/RDP). The instance by default gets a root storage volume (EBS). The diagram above illustrates these components in a basic EC2 setup.
```

```
Introduction to Amazon EC2 (Elastic Compute Cloud)

Amazon Elastic Compute Cloud (EC2) is AWS’s core Infrastructure-as-a-Service (IaaS) offering that provides on-demand, resizable compute capacity in the cloud
docs.aws.amazon.com
. In simple terms, EC2 lets you launch virtual machines (called instances) on AWS’s global infrastructure. You have full control over the operating system and software on these instances, and you pay only for the compute time you use
aws.amazon.com
. EC2 is designed to easily scale up or down – you can quickly provision more servers during peak demand and shut them down when they’re no longer needed, enabling highly flexible “web-scale” computing
aws.amazon.com
. As part of the AWS ecosystem, EC2 often works alongside other services (for example, an application might run on EC2 but store data in Amazon S3 or use an AWS database service). This flexibility and integration make EC2 a fundamental building block in many cloud architectures
```

```
Amazon S3 Guide for AWS Solutions Architect – Associate (SAA) Exam
What is Amazon S3 and How It Fits into AWS
Amazon Simple Storage Service (S3) is a highly scalable object storage service in AWS. It allows you to store and retrieve unlimited amounts of data, from anywhere on the web, with high durability (designed for 99.999999999% durability, or “11 nines”
aws.amazon.com
) and availability. In the AWS ecosystem, S3 serves as a core storage backbone for a variety of use cases: data lakes, backups, archives, websites, mobile apps, IoT data, big data analytics, and more.

S3 is integrated with many other AWS services (like EC2, Lambda, Athena, Redshift, CloudTrail, etc.), making it a fundamental building block for architectures. It provides virtually infinite storage capacity and offloads the management of hardware, replication, and scaling to AWS.
```

```
Tip: Always prefer using Auto Scaling Groups (ASGs) with Elastic Load Balancers (ELBs) for high availability and fault tolerance.
```
