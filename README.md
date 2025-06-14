<h1>3-Tier Web Application on AWS</h1>

A scalable, highly available web application built using AWS services following the traditional 3-tier architecture pattern.

Architecture Overview

This application follows a 3-tier architecture pattern deployed on AWS:

Amazon Route 53: DNS service for hosted zone

Amazon CloudFront: Global CDN for static content delivery and use ALB as origin  

AWS Cerificate Manager: create public certificate to use HTTPS


<h3>Front-end Tier</h3>

Application Load Balancer (ALB): Distributes incoming traffic to web servers

Amazon EC2 Auto Scaling Group: Web servers hosting the frontend application


<h3>Back-end Tier</h3>

Application Load Balancer (ALB): Internal load balancer for application servers

Amazon EC2 Auto Scaling Group: Application servers running business logic


<h3>Database Tier</h3>

Amazon RDS: Primary relational database with Multi-AZ deployment


<h1>Infrastructure Components</h1>
<h3>Network & Security</h3>

Amazon VPC: Isolated network environment

Public Subnets: Web servers and load balancers

Private Subnets: Application servers and databases

NAT Gateway: Outbound internet access for private resources

Security Groups: Network-level firewall rules

AWS WAF: Web application firewall protection


<h3>Monitoring & Logging</h3>

Amazon CloudWatch: Metrics, alarms, and dashboards

Amazon CloudWatch Logs: Centralized log management


<h3>Connection</h3>

AWS SSM : start remote sessions to VMs

<h1>Deployment Instructions</h1>
Manual Deployment

1. Network Setup
VPC

2 Application Load Balancer : internet-facing load balancer & internal load balancer

Internet Gateway

2 availability zones : 2 public subnets & 6 private subnets

Route Tables

Security Groups : Internet-Facing ALB-SG & Internal ALB-SG & FRONT-END-SG & BACK-END-SG & PRIMARY_RDS-SG & STANDBY_RDS-SG

DB subnet group for RDS


1. Compute Setup

Front-End Auto Scaling Group

Back-End Auto Scaling Group


3. Database Setup

Primary RDS Instance (mysql engine)

Standby RDS Instance (mysql engine)


5. Monitoring Setup

install CLoudWatch Agent


6. CDN Setup

CloudFront Distribution with ALB as origin


7. Domain Setup

create hosted zone with Route 53


8. Certificate Setup

create public certificate from ACM


Security Best Practices
Network Security

Web servers in public subnets with limited access

Application servers in private subnets

Database servers in isolated private subnets

Security groups with principle of least privilege


Data Protection

RDS encryption at rest and in transit

IAM roles with minimal required permissions

                CloudWatchFullAccess

                AmazonSSMFullAccess

                AmazonEC2RoleforSSM

                CloudWatchAgentAdminPolicy

                CloudWatchAgentServerPolicy

                AmazonSSMManagedInstanceCore


Database Scaling

Read replicas for read-heavy workloads

Connection pooling for efficient database connections


Monitoring & Alerts

CloudWatch Alarms

CPU utilization > 80%

Memory utilization > 85%


Backup & Disaster Recovery

Database Backups

Automated daily backups with 7-day retention

Point-in-time recovery enabled


Application Backups

EC2 AMI snapshots for server images


<h1>3-Tier Web Application Architecture</h1>
<img src = "https://github.com/mshaf3ey/AWS-2-Becoming-a-Solutions-Architect/blob/main/Manara.drawio.png" />
