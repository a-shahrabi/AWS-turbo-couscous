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
