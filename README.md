# AWS-turbo-couscous

# AWS Project

The IAM Mental Model
Think of IAM like a company's security system:

Users = Employees with ID badges
Groups = Departments (Marketing, Engineering)
Roles = Temporary access cards for contractors/services
Policies = The rules about who can enter which rooms

Compute

EC2: Instance types, placement groups, AMIs, user data, metadata
Lambda: Triggers, limits (15 min timeout, 10GB memory), environment variables
ECS/Fargate: Container orchestration basics
Elastic Beanstalk: Quick deployment platform

Storage

S3: Storage classes (Standard, IA, Glacier), lifecycle policies, versioning, encryption
EBS: Volume types (gp3, io2, st1, sc1), snapshots, encryption
EFS: Shared file system for Linux, performance modes
Storage Gateway: File, Volume, and Tape Gateway types

Database

RDS: Multi-AZ vs Read Replicas, automated backups, encryption
DynamoDB: Partition/sort keys, GSI/LSI, on-demand vs provisioned
Aurora: MySQL/PostgreSQL compatible, serverless option
ElastiCache: Redis vs Memcached use cases

Cost Optimization
Use the right instance types for the job. Many people default to general-purpose instances, but compute-optimized (C5) or memory-optimized (R5) instances often provide better price-performance for specific workloads. Always check the AWS calculator and consider Reserved Instances or Spot instances where appropriate.
Implement lifecycle policies everywhere. Set up S3 lifecycle rules to automatically transition data to cheaper storage classes (IA, Glacier) and delete old logs. Configure RDS automated backups with appropriate retention periods rather than keeping everything forever.


Security Best Practices
Never hardcode credentials. Use IAM roles for EC2 instances, Lambda functions, and other services. Store secrets in AWS Secrets Manager or Parameter Store with encryption. Rotate credentials regularly using automated processes.
Apply the principle of least privilege religiously. Start with minimal permissions and add only what's needed. Use AWS Config rules to monitor for overly permissive policies and regularly audit IAM permissions with Access Analyzer.

Architecture Patterns
Design for failure from day one. Deploy across multiple Availability Zones, implement health checks, and use Auto Scaling Groups. Plan for what happens when each component fails - your database, load balancer, or entire AZ going down.
Embrace serverless where it makes sense. Lambda functions with API Gateway can replace simple web applications at a fraction of the cost and operational overhead. Use Step Functions for complex workflows instead of managing your own orchestration.

Concentrate on building strong foundational knowledge of key AWS services like EC2, Lambda, S3, DynamoDB, CloudFront, and RDS, particularly how to use them for reducing costs and improving performance.
While you should understand these essential services deeply, you don't need to memorize exact numbers or default configurations. The goal is to learn how to properly integrate these services into well-designed system architectures.
