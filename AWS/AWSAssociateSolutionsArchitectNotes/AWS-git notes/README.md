Notes for preparing for AWS Certified Solutions Architect - Associate


## Resources
- [Certification Home](https://aws.amazon.com/certification/certification-prep/)
- [Exam Guide Blueprint](http://awstrainingandcertification.s3.amazonaws.com/production/AWS_certified_solutions_architect_associate_blueprint.pdf)
- [Open Guide to Amazon Web Services](https://github.com/open-guides/og-aws)
- [Resources to Prepare for AWS Certifications](https://gist.github.com/leonardofed/bbf6459ad154ad5215d354f3825435dc)
- [AWS Documentation](https://aws.amazon.com/documentation/)
- [AWS Whitepapers](https://aws.amazon.com/whitepapers/) 
- [AWS FAQs](https://aws.amazon.com/faqs/) 


## Whitepapers

Specific whitepapers called out in either the Exam Guide Blueprint or the Certification Prep homepage:

#### [Overview of Amazon Web Services](https://d0.awsstatic.com/whitepapers/aws-overview.pdf)
* Compute
   * EC2
      * IaaS / Virtual Machines
      * Elastic / scalable
      * Pricing
         * On demand (highest cost, pay as you go by the hour)
         * Reserved (1-3 yr commitment for resources, up to 75% discount from on-demand)
         * Spot (bid marketplace for unused AWS capacity, can be take away if pricing goes above your maximum)  
   * Elastic Load Balancing (ELB)
   * AWS Lambda - Functions as a Service / Serverless
      * Upload code, create triggers, only pay for actual compute time
   * EC2 Container Service (ECS)
      * Container management that support Docker
   * Elastic Beanstalk
      * PaaS that supports Java, .NET, PHP, Node.js, Python, Ruby, Go, and Docker
* Storage and Content Delivery
   * S3
      * HTTP based object-store
      * Durable key-value store
   * Glacier
      * Archive storage for infrequently accessed data 
   * Elastic Block Store (EBS)
      * Block storage for EC2 Virtual Machines
   * Elastic File System (EFS)
      * Shared file system (NFS)
   * Storage Gateway
      * Appliance you install on-premise, tiers to S3 and Glacier 
   * Cloud Front
      * CDN to front and cache other AWS services (EC2, S3, etc)
   * Snowball
      * Suitcase used to get large amounts of data to AWS
* Database
   * Amazon RDS (Relational Database Service)
      * Fully managed
      * Aurora, MySQL, Oracle, MS SQL, PostgreSQL, MariaDB
      * Aurora is MySQL compatable, higher performing / lower cost
   * DynamoDB
      * NoSQL, Key/value store
   * Redshift
      * Data Warehouse
   * ElastiCache
      * Managed in-memory cache
      * Supports both Memcached and Redis
* Networking
   * VPC (Virtual Private Cloud)
      * Isolated network environment
      * You control all in/out, IPs, routing, etc
   * Direct Connect
      * Private connectivity via dedicated circuit
   * Route 53
      * DNS service
* Developer Tools
   * CodeCommit
      * Source control, managed Git
   * CodeDeploy
      * Automated code deployments
   * CodePipeline
      * CI/CD service
* Management Tools
   * CloudWatch
      * Monitoring service for AWS components
   * CloudFormation
      * Templated deployments
   * CloudTrail
      * Audit logs of AWS actions
   * AWS Config
      * Configuration and Inventory Management
      * Enables compliance auditing and security analysis
   * OpsWorks
      * Managed Chef
   * Service Catalog
     * Create and manage list of approved services for your org
   * Trusted Advisor
      * Analysis and recommends changes to your environment, to save money or improve performance and availability
* Security and Identify
   * Identity and Access Management (IAM)
      * Manage users/roles/access to AWS services
   * Key Management Service (KMS)
      * Managment of encryption keys
   * Directory Service
      * Managed MS or Samba Active Directory 
   * Inspector
      * Security and Vulnerability Compliance
   * WAF (Web Application Firewall)
   * CloudHSM
      * Hardware Security Module for managing encryption keys
* Analytics
   * Amazon EMR (Elastic Map Reduce)
      * Big Data
      * Hadoop, Spark, Presto 
   * QuickSight
      * Business Intelligence
   * AWS Data Pipeline
   * ElasticSearch Service
   * Kinesis
      * Ingestion and analysis of stream data
   * Amazon Machine Learning (Amazon ML)
* Application
  * API Gateway
  * Elastic Transcoder
    * media (video) transcoding
  * Simple Email Service (SES)
  * Simple Queue Service (SQS)
  * Simple Workflow
    * run background jobs
  * Simple Notification Service (SNS)
    * send push notifications, email, and SMS messages
 * Enterprise Applications
   * Workspaces
     * managed desktops
   * Workdocs
     * document storage and sharing
   * Workmail
     * managed outlook
       
      
#### [Overview of Security Processes](https://d0.awsstatic.com/whitepapers/Security/AWS_Security_Whitepaper.pdf)
* Shared Security Model
  * Security IN Cloud (customer)
  * Security OF Cloud (AWS)
* Infrastructure Security
  * Compliance Programs
    * SOC, FISMA, DIACAP, FedRAMP, DOD, PCI, ITAR, FIPS, etc, etc
  * Business Continuity
    * Availability
      * Regions, Availability Zones, Datacenters
  * Network Security
    * AWS mitigates: DDoS, MITM, IP Spoofing, Port Scanning, Packet Sniffing by other tenants
* Account Security Features
  * Credentials
    * Passwords
    * MFA
    * Access keys (used with API)
    * Key pairs (used with ssh and EC2)
    * x.509 (SOAP)
  * Individual User Accounts
    *  individual, system, or application that interacts with AWS
resources, either programmatically or through the AWS Management Console
* Service-Specific Security
  * Compute
    * Xen hypervisor
    * Instance isolation
    * firewall is default deny
    * EBS volumes are redudantly stored in same AZ
      * recommend regular backups to S3
    * EBS volumes can be encrypted when used with more powerful EC2 instance types
  * Networking
    * ELB can terminate ssl
    * VPC
      * Security groups, ACLs, route tables, external gateways
      * Must create VPC specific security groups, can't reuse EC2 groups
      * Can created 'dedicated' VPC so all instanced within are created on single-tenant hardware
    * Can connect upto two virtual nics (ENI - elastic network interface) to an instance
    * CloudFront
      * Offers no durability.  Use s3 to store origin.
      * Can enable 'private content' to control who downloads
  * Storage
    * S3
      * Can control access via: IAM, ACL, or Bucket Policy
      * SSL endpoints
      * Supports both server-side and client-side encryption
      * Can enable CORS for static hosting
    * Glacier
      * Clients have to compute and supply tree hash when uploading files
      * Files in S3 can be moved to Glacier via lifecycle settings
      * Retrieval of files takes 3-5 hours
      * Data is automatically encrypted in Glacier
    * Storage Gateway
      * Runs as a VM on VMWare
      * Gateway-stored volumes
        * Stored locally and backed up to S3
      * Gateway-cached volumes
        * Data stored in S3, cached locally
      * Gateway-Virtual Tape Library
        * Connect to existing backup solution
    * Import/Export
      * Your portable storage device you ship to AWS
  * Database
    * DynamoDB
      * Automatically replicated across multiple AZs
      * set up automatic backups using a special template in AWS Data Pipeline
    * RDS
      * Supports transport encryption via SSL or TDE
      * automatic backups enable point in time recovery
      * on demand snapshots
      * AWS handles patching in a maintenance window you control
    * Redshift
      * support encryption at rest
      * AWS handles pathing in announced maintenance windows

  


#### [Risk & Compliance](https://d0.awsstatic.com/whitepapers/compliance/AWS_Risk_and_Compliance_Whitepaper.pdf)



#### [Storage Services Overview](https://d0.awsstatic.com/whitepapers/Storage/AWS%20Storage%20Services%20Whitepaper-v9.pdf)

* S3 - object
  * Usage
    * store static web content and media
    * host static web sites
    * data store for computation and large-scale analytics
    * backups
  * Durability - 11 9s
  * Availability - 4 9s
  * Default syced across AZs can be replicated across Regions
  * REST/HTTP interface, AWS CLI, SDKs
* Glacier - archive
  * Usage
    * Archive
    * Tape replacement
* EFS - file
  * Usage
    * shared file storage NFS
  * Replicated across AZs
* EBS - persistant block storage
  * Usage
    * VM disks
  * Typical failure rate of .2%
  * Take frequent stapshots
* EC2 Instance Storage - temp block storage
  * Usage
    * temporary storage on VM
  * Lost when VM is deleted
* Storage Gateway - onprem appliance
  * VM ran on VMWare
  * Synced to AWS
  * exposes iSCSI interface
* Snowball - offline transport
* CloudFront - CDN
  * Usage
    * static content cache
    


#### [Architecting for the Cloud: AWS Best Practices](https://d0.awsstatic.com/whitepapers/AWS_Cloud_Best_Practices.pdf)

* Scalability
  * Virtical
    * stop instance, choose new instance type
  * Horizontal
    * Deploy more servers
    * Need app design around stateless
    * or communicate state through session cookie
    * store shared components on EFS/S3/database
    * or configure ELB for session affinity
* Disposable Resources
  * immutable infrastructure - when change or problem throw away and create new
  * How
    * Bootrapping cloud-init or config mgmnt tool (opsworks)
    * Golden images
  * Infrastructure as code
* Loose Coupling
  * break application into pieces
  * Interfaces
    * REST APIs
  * Service Discovery
    * use ELB to create stable end point names
  * Asynchronous Integration
    * allowing queuing in the event of failures or delays
* Serivces, Not servers
  * Looks for opportunies to replace IaaS with managed AWS services
* Databaess
  * RDS for transactions that require joins or complexity
  * NoSQL for primarily indexes and queries
* Removing single points of failure
  * redundancy
  * health checks
  * deploy in multiple AZs
* Optimize for cost
  * right-size, grow resources on demand



#### [Security Best Practices](https://d0.awsstatic.com/whitepapers/Security/AWS_Security_Best_Practices.pdf)



#### [Cloud Architectures](https://d0.awsstatic.com/whitepapers/aws-cloud-architectures.pdf)



#### [Development and Test on AWS](https://d0.awsstatic.com/whitepapers/aws-development-test-environments.pdf)



#### [Backup and Recovery Approaches Using AWS](https://d0.awsstatic.com/whitepapers/Storage/Backup_and_Recovery_Approaches_Using_AWS.pdf)


#### [Amazon Virtual Private Cloud Connectivity Options](https://d0.awsstatic.com/whitepapers/aws-amazon-vpc-connectivity-options.pdf)

* Network to AWS VPC Connectivity Options
  * Hardware VPN
  * Direct Connect
    * VLAN between AWS and WAN partner
  * Direct Connect + VPN
  * VPN CloudHub
    * Use AWS to route between and connect your locations
  * Software VPN
    * 3rd party soft appliance inside VPC
* VPC to VPC Connectivity Options
  * VPC Peering
    * AWS provided, no VPN instances
  * Sofware VPN
    * Managed by you, 3rd party
  * Software to Hardware VPN
  * Hardware VPN
  * Direct Connect
* Internal User to VPC Connectivity Options
  * Software Remote Access VPN

#### [How AWS Pricing Works](https://d0.awsstatic.com/whitepapers/aws_pricing_overview.pdf)

#### [Disaster Recovery](https://d0.awsstatic.com/whitepapers/aws-disaster-recovery.pdf)

* Recovery Time Objective and Recovery Point Objective
  * RTO -  time it takes after a disruption to restore a business process
  * RPO -  acceptable amount of data loss measured in time (the data lost between failure and previous backup)
* Disaster Recovery Scenarios (slowest to quickest)
  * Backup and Restore
    * traditional backup to offsite (S3), restore to on-prem or EC2
  * Pilot Light
    * Minimal version of infrastructure running in AWS
    * Usually DB that is replicated to RDS
    * Other systems as AMIs ready for deployment
  * Warm Standby
    * Fully functional scaled down version running in AWS
    * Minimal scale, can be scaled up for prod
  * Multi-Site (AWS and On-site)
    * Active-Active
    * DNS for distribution
  * AWS Prod to AWS DR using Regions
    * Instead of on-site use AWS for all

#### [Deployment Options](https://d0.awsstatic.com/whitepapers/overview-of-deployment-options-on-aws.pdf)
* Deployment Services
  * Elastic Beanstalk
    * Fast and simple PaaS
    * PHP, Java, Python, Ruby, Node.js, .NET,Go, or Docker
    * auto scaling, ELB
  * CloudFormation
    * Define AWS infrastructure in templates
    * infrastructure as code
  * OpsWorks
    * configuration management - Chef
  * CodeCommit
    * private Git repos
  * CodePipeline
    * CI/CD
    * build, stage, test, deploy
  * CodeDeploy
    * managed code deployments
  * EC2 Container Service
    * Container orchestration on EC2
* Strategies for updating
  * Prebaked AMIs
    * Load all binaries on preconfigured AMIs
    * Makes autoscaled deployments faster
  * In-place
    * Upgrade live running instances
    * Use codedeploy/opsworks
  * Disposable
    * Create new instances with updated code, destroy old
  * Blue-Green
    * Create new identical stack, upgrade, cutover
    * zero downtime 

## FAQs
Specific FAQs called out in either the Exam Guide Blueprint or the Certification Prep homepage:

* [Amazon EC2](https://aws.amazon.com/ec2/faqs/)
* [Amazon S3](https://aws.amazon.com/s3/faqs/)
* [Amazon VPC](https://aws.amazon.com/vpc/faqs/)
* [Amazon Route 53](https://aws.amazon.com/route53/faqs/)
* [Amazon RDS](https://aws.amazon.com/rds/faqs/)
* [Amazon SQS](https://aws.amazon.com/sqs/faqs/)

## Specific Topics to Know
* [Auto Scaling](https://github.com/open-guides/og-aws#auto-scaling)
* [CloudWatch](https://github.com/open-guides/og-aws#cloudwatch)
* [IAM](https://github.com/open-guides/og-aws#security-and-iam)
* [Load Balancers](https://github.com/open-guides/og-aws#load-balancers)
* [High Availability](https://github.com/open-guides/og-aws#high-availability)
* [VPC Basics](https://github.com/open-guides/og-aws#vpc-basics)

## Hands on Practice

[Qwiklabs Quest - Solutions Architect](https://qwiklabs.com/quests/10?locale=en)



