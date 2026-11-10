# 30-Day AWS Solutions Architect -- Job & Exam Ready Roadmap

> **Goal:** Prepare for the AWS Certified Solutions Architect --
> Associate (SAA-C03) exam while building practical skills for AWS
> Solution Architect and DevOps-oriented roles.

This is an intensive 30-day learning plan designed for learners with
some AWS/DevOps exposure. It emphasizes architecture decisions, hands-on
implementation, security, high availability, disaster recovery,
scalability, and cost optimization---not just memorizing services.

## Course at a Glance

  -----------------------------------------------------------------------
  Area                                Target
  ----------------------------------- -----------------------------------
  Duration                            30 days

  Suggested daily commitment          3--4 hours

  Certification target                AWS Certified Solutions Architect
                                      -- Associate (SAA-C03)

  Practical work                      5+ architecture projects

  Interview preparation               Scenario-based questions and
                                      architecture discussions

  Final outcome                       Exam preparation plus a portfolio
                                      of documented AWS designs
  -----------------------------------------------------------------------

**Important:** Passing the certification exam is not guaranteed by
completing a 30-day plan. Use practice-exam performance and hands-on
understanding to decide when you are ready to book the exam.

------------------------------------------------------------------------

## 1. 30-Day Syllabus

### Week 1 --- AWS Core Infrastructure and Networking

  -----------------------------------------------------------------------
  Day                     Topics                  Practical lab
  ----------------------- ----------------------- -----------------------
  1                       AWS Global              Sketch a multi-AZ AWS
                          Infrastructure,         architecture
                          Regions, Availability   
                          Zones, Edge Locations,  
                          Shared Responsibility   
                          Model                   

  2                       IAM users, groups,      Create least-privilege
                          roles, policies, STS,   IAM roles and policies
                          MFA                     

  3                       VPC, CIDR,              Build a custom VPC
                          public/private subnets, 
                          route tables            

  4                       Internet Gateway, NAT   Configure
                          Gateway, VPC Peering,   private-subnet
                          VPC Endpoints           connectivity

  5                       Security Groups,        Secure and troubleshoot
                          Network ACLs, VPC Flow  a VPC
                          Logs                    

  6                       Route 53, DNS, hosted   Configure DNS and HTTPS
                          zones, routing          for a test application
                          policies, ACM           

  7                       ALB, NLB, target        Deploy a highly
                          groups, Auto Scaling,   available web tier
                          launch templates        
  -----------------------------------------------------------------------

**Week 1 outcome:** Explain how traffic travels from the internet to an
application in private subnets, and design a secure multi-AZ VPC.

### Week 2 --- Compute, Storage, and Database Architecture

  -----------------------------------------------------------------------
  Day                     Topics                  Practical lab
  ----------------------- ----------------------- -----------------------
  8                       EC2, instance families, Launch and configure
                          EBS, AMIs, placement    EC2 instances
                          groups                  

  9                       Auto Scaling, ALB,      Build an auto-scaling
                          scaling policies,       web tier
                          health checks           

  10                      S3, versioning,         Configure secure S3
                          lifecycle rules,        storage
                          replication, encryption 

  11                      EFS, FSx, EBS, Storage  Compare block, file,
                          Gateway                 and object storage

  12                      RDS, Multi-AZ, read     Design a highly
                          replicas, Aurora        available relational
                                                  database

  13                      DynamoDB, DAX,          Design a low-latency
                          ElastiCache, Redis      data layer

  14                      AWS Backup, snapshots,  Create and test a
                          disaster recovery, RPO, backup/recovery plan
                          RTO                     
  -----------------------------------------------------------------------

**Week 2 outcome:** Choose appropriately between EC2 and Lambda, RDS and
DynamoDB, Multi-AZ and read replicas, and EBS, EFS, and S3.

### Week 3 --- Advanced Architecture, Security, and Scalability

  -----------------------------------------------------------------------
  Day                     Topics                  Practical lab
  ----------------------- ----------------------- -----------------------
  15                      CloudFront, edge        Put a static or web
                          locations, regional     application behind
                          edge caches, origins    CloudFront

  16                      AWS WAF, Shield, KMS,   Apply security controls
                          Secrets Manager, ACM    to a web application

  17                      Lambda, API Gateway,    Build a small
                          SQS, SNS                serverless workflow

  18                      EventBridge, Step       Design an event-driven
                          Functions, Kinesis      workflow

  19                      ECS, ECR, EKS, Fargate  Deploy a containerized
                                                  application

  20                      CloudWatch, CloudTrail, Configure monitoring,
                          AWS Config, Systems     audit, and compliance
                          Manager                 visibility

  21                      AWS Organizations,      Design a multi-account
                          Control Tower, SCPs,    environment
                          IAM Identity Center     
  -----------------------------------------------------------------------

**Week 3 outcome:** Explain and design cloud-native, serverless,
containerized, monitored, and secure systems.

### Week 4 --- Real-World Architecture, Projects, and Exam Preparation

  -----------------------------------------------------------------------
  Day                     Topics                  Practical project
  ----------------------- ----------------------- -----------------------
  22                      AWS Well-Architected    Review an architecture
                          Framework and its six   against the framework
                          pillars                 

  23                      High availability,      Design a highly
                          fault tolerance,        available application
                          Multi-AZ, Multi-Region  

  24                      Disaster recovery,      Design a disaster
                          backups, failover,      recovery solution
                          RPO/RTO                 

  25                      Cost Explorer, AWS      Review and optimize
                          Budgets, Savings Plans, infrastructure costs
                          Reserved Instances      

  26                      Migration strategies,   Design an
                          DMS, DataSync,          on-premises-to-AWS
                          Snowball, hybrid cloud  migration

  27                      Infrastructure as Code: Deploy infrastructure
                          CloudFormation and      using Terraform
                          Terraform               

  28                      End-to-end production   Build and document a
                          architecture            three-tier application

  29                      SAA-C03 practice exams  Take a timed mock exam
                          and scenario questions  and review weak areas

  30                      Final assessment and    Present and defend an
                          architecture interview  architecture design
  -----------------------------------------------------------------------

------------------------------------------------------------------------

## 2. Five Portfolio Projects

For every project, document the business requirements, architecture
diagram, service choices, security controls, availability, recovery
strategy, estimated costs, deployment steps, and trade-offs.

### Project 1 --- Highly Available Three-Tier Architecture

**Suggested components** - Route 53 and optionally CloudFront -
Application Load Balancer - EC2 Auto Scaling across multiple
Availability Zones - RDS Multi-AZ - Public and private subnets -
Security Groups, IAM roles, and CloudWatch

**Demonstrates:** Production architecture, networking, scaling, and high
availability.

### Project 2 --- Multi-Region Disaster Recovery

**Suggested components** - Primary and recovery AWS Regions - RDS
backup/replication strategy appropriate to the recovery objective - S3
cross-Region replication - Route 53 failover routing - Documented
recovery runbook

**Demonstrates:** Disaster recovery planning, RPO/RTO decisions, and
regional resilience.

### Project 3 --- Serverless Application

**Suggested components** - API Gateway - Lambda - DynamoDB - SQS and
SNS - CloudWatch

**Demonstrates:** Event-driven design, decoupling, and serverless
architecture.

### Project 4 --- Secure Enterprise Architecture

**Suggested components** - IAM least-privilege policies and roles - AWS
WAF and appropriate Shield protections - KMS encryption - Secrets
Manager - CloudTrail and AWS Config - Private networking and controlled
egress

**Demonstrates:** Cloud security, governance, encryption, and
auditability.

### Project 5 --- Container-Based Microservices Architecture

**Suggested components** - ECR - ECS or EKS (choose based on the project
requirements) - Application Load Balancer - Auto Scaling - RDS or
another suitable data store - CI/CD pipeline and CloudWatch

**Demonstrates:** Containers, deployment automation, scalability, and
operations.

------------------------------------------------------------------------

## 3. Daily Study Schedule

  Activity                              Suggested time
  ----------------------------------- ----------------
  Concepts and architecture lessons         60 minutes
  AWS Console / CLI practical lab           90 minutes
  Exam scenario questions                   30 minutes
  Interview preparation                     30 minutes
  Revision and architecture drawing         30 minutes
  **Total**                                **4 hours**

If you have only two hours per day, prioritize the day's core concepts
and lab, then extend the plan beyond 30 calendar days rather than
skipping practical work.

------------------------------------------------------------------------

## 4. Certification Preparation --- SAA-C03

**Target:** AWS Certified Solutions Architect -- Associate (SAA-C03)

The exam guide is the authority for current exam details. Check it
before booking because exam policies, pricing, and content can change.

### Exam format (verify against the current official guide)

  Detail           Information
  ---------------- -----------------------------------------------------
  Exam duration    130 minutes
  Questions        65
  Passing score    720 out of 1000
  Question types   Multiple choice and multiple response
  Exam fee         Check current regional pricing on AWS Certification

### Exam domains and approximate weights

  Domain                                   Weight
  -------------------------------------- --------
  Design Secure Architectures                 30%
  Design Resilient Architectures              26%
  Design High-Performing Architectures        24%
  Design Cost-Optimized Architectures         20%

Security has the largest weighting in this outline. Give IAM,
encryption, network security, data protection, and access control
consistent attention.

### Exam readiness checklist

-   [ ] Read the official SAA-C03 exam guide.
-   [ ] Understand the four exam domains and their objectives.
-   [ ] Complete hands-on labs for core services.
-   [ ] Practice scenario-based questions; understand why each
    distractor is wrong.
-   [ ] Take timed practice exams.
-   [ ] Review every incorrect answer and revisit weak topics.
-   [ ] Book the exam only when practice results are consistently strong
    and concepts are understood.

------------------------------------------------------------------------

## 5. Recommended Learning Resources

1.  **[AWS Skill Builder](https://skillbuilder.aws/)** --- Official AWS
    learning and exam preparation.
2.  **[AWS Documentation](https://docs.aws.amazon.com/)** --- Service
    documentation, configuration guides, and tutorials.
3.  **[AWS Architecture Center](https://aws.amazon.com/architecture/)**
    --- Reference architectures and design guidance.
4.  **[AWS Well-Architected
    Framework](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html)**
    --- Best practices across the six pillars.
5.  **[Official SAA-C03 Exam
    Guide](https://docs.aws.amazon.com/aws-certification/latest/solutions-architect-associate-03/solutions-architect-associate-03.html)**
    --- Current exam scope and objectives.

Use official documentation to confirm service behavior and exam
objectives. Third-party videos and question banks can supplement
learning, but should not replace the official exam guide or hands-on
practice.

------------------------------------------------------------------------

## 6. How to Study Each Day

For each daily topic, follow this repeatable lesson structure:

1.  **Concepts:** Learn what the service does and which problem it
    solves.
2.  **Architecture:** Draw the service in an architecture diagram and
    trace request/data flow.
3.  **Real-world use case:** Identify the business requirement that
    would justify the service.
4.  **Service comparison:** Explain why you would choose it over
    alternatives.
5.  **Hands-on lab:** Deploy, configure, monitor, and troubleshoot it.
6.  **Security:** Review IAM, network exposure, encryption, logging, and
    secrets.
7.  **Exam practice:** Attempt scenario-based questions and explain the
    reasoning.
8.  **Interview practice:** Answer design and troubleshooting questions
    aloud.
9.  **Homework:** Record what worked, what failed, and what you would
    improve.

### Questions to ask for every AWS service

-   What problem does this service solve?
-   When should a company use it?
-   What are the alternatives?
-   What are the availability and failure considerations?
-   How is it secured?
-   What are the cost drivers?
-   How would I monitor and troubleshoot it?

------------------------------------------------------------------------

## 7. GitHub Repository Structure

As you progress, use a structure like this:

``` text
aws-solutions-architect-30-days/
├── README.md
├── week-01-core-infrastructure/
│   ├── day-01-global-infrastructure.md
│   ├── day-02-iam.md
│   ├── day-03-vpc.md
│   └── ...
├── week-02-compute-storage-databases/
│   └── ...
├── week-03-security-and-advanced-services/
│   └── ...
├── week-04-architecture-and-exam/
│   └── ...
├── projects/
│   ├── 01-three-tier-ha/
│   ├── 02-multi-region-dr/
│   ├── 03-serverless/
│   ├── 04-secure-enterprise/
│   └── 05-container-microservices/
├── diagrams/
├── labs/
├── interview-questions/
└── exam-preparation/
```

### Suggested daily GitHub update

For each day, commit: - Notes and key concepts - Architecture diagram -
Lab steps and commands (remove credentials and secrets) - Screenshots
where useful (redact account IDs and sensitive information) - Errors
encountered and their fixes - Exam questions you got wrong and the
correct reasoning

Example commit messages:

``` bash
git add .
git commit -m "Day 03: Build custom VPC with public and private subnets"
git push
```

------------------------------------------------------------------------

## 8. Cost and Security Guardrails for Labs

AWS labs can create charges. Before starting:

-   Set an AWS Budget and billing alerts.
-   Use the smallest suitable resources.
-   Prefer short-lived lab environments.
-   Stop or terminate EC2 instances when finished.
-   Delete unused load balancers, NAT Gateways, EIPs, databases,
    snapshots, and other billable resources when no longer needed.
-   Check S3 storage, data transfer, and CloudWatch costs.
-   Never commit AWS access keys, passwords, private keys, `.env` files,
    or unredacted account details to GitHub.
-   Use IAM roles and temporary credentials where possible.
-   Review the pricing page for each service before deploying it.

**Note:** The AWS Free Tier does not mean every service or configuration
is free.

------------------------------------------------------------------------

## 9. Final 30-Day Completion Checklist

-   [ ] Explain AWS global infrastructure and shared responsibility.
-   [ ] Design a VPC with public/private subnets and controlled routing.
-   [ ] Apply IAM least privilege and encryption.
-   [ ] Design compute, storage, and database tiers.
-   [ ] Explain load balancing and Auto Scaling.
-   [ ] Design highly available and disaster recovery solutions.
-   [ ] Build a serverless or event-driven workflow.
-   [ ] Explain container deployment options.
-   [ ] Configure monitoring, logging, and auditing.
-   [ ] Estimate and optimize AWS costs.
-   [ ] Complete and document at least three end-to-end projects (five
    is the target).
-   [ ] Complete timed SAA-C03 practice exams and review weak areas.
-   [ ] Present an architecture and explain its trade-offs in an
    interview.

## Closing Advice

Do not learn AWS services only to memorize their definitions. Learn to
answer:

> **Why would a company choose this service, and why would it choose it
> over an alternative?**

That decision-making ability---supported by hands-on labs, clear
diagrams, security awareness, cost reasoning, and operational
experience---is central to becoming a job-ready AWS Solutions Architect.

------------------------------------------------------------------------

## Disclaimer

This repository is a personal learning roadmap, not an official AWS
course or a guarantee of certification or employment. AWS service
features, exam objectives, and prices can change. Always verify current
details in official AWS documentation before making decisions or
deploying resources.
