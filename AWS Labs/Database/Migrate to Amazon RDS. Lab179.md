# AWS Challenge Lab: Migrating to Amazon RDS

<img width="422" height="123" alt="image" src="https://github.com/user-attachments/assets/b8897520-0e69-445f-9dc7-005274c63117" />

## Hey! Welcome to My AWS Lab Journey 👋

You're looking at the documentation for an AWS Challenge Lab I completed, where I migrated a café web application from a local MySQL database to a fully managed Amazon RDS instance. It was a hands-on exercise that pushed me to understand database migration strategies, AWS networking, and infrastructure automation using the AWS CLI.
<img width="501" height="490" alt="image" src="https://github.com/user-attachments/assets/3700f7cf-0368-4922-bfbf-fbfb0c6d1e55" />

THE AIM/OBJECTIVE
<img width="874" height="460" alt="image" src="https://github.com/user-attachments/assets/35af064b-8d3a-4b79-be05-e913e82eae72" />



## What I Set Out to Do

The challenge was straightforward but required real execution:

1. **Generate test data** on the existing local database to have something meaningful to migrate
2. **Build RDS infrastructure** using AWS CLI—security groups, private subnets, and the database instance itself
3. **Migrate the database** using mysqldump and restore it to the new RDS instance
4. **Reconfigure the application** to point to the new managed database
5. **Monitor performance** using CloudWatch metrics integrated with RDS

No shortcuts, no copy-paste solutions—just me, the AWS CLI, and a production-ready database migration to execute.

---

## How I Tackled It

### Getting Started: Establishing the Baseline

First thing I did was fire up the AWS lab environment and access the café web application. I placed several orders through the website to generate real transactional data in the local database. This gave me actual data to migrate and a baseline to verify the migration's success.

**Figure 1: Café website with order data ready for migration**
<img width="934" height="461" alt="image" src="https://github.com/user-attachments/assets/d4aeed74-fd2f-4f42-ba1d-4dcbf9359dd7" />

<img width="856" height="424" alt="image" src="https://github.com/user-attachments/assets/4b69fe93-91dd-4df9-92e7-c71adbccaece" />



### Connecting: SSH into the CLI Host

I used EC2 Instance Connect to access the CLI Host instance—my command center for this entire operation. After connecting, I configured the AWS CLI with my access credentials, setting the region and output format to JSON. This instance would be my interface to AWS services throughout the migration.

**Figure 2: Successfully connected and AWS CLI configured**

<img width="921" height="179" alt="image" src="https://github.com/user-attachments/assets/8843b494-8e72-43c1-9683-a8dfa9b207f5" />

<img width="912" height="368" alt="image" src="https://github.com/user-attachments/assets/af66af6c-4cb5-42e7-b512-b65c856cc827" />



### Building the Foundation: Creating RDS Prerequisites

Now came the infrastructure work. I couldn't just spin up an RDS instance—I needed to build the entire networking and security foundation first.

Here's what I built using pure AWS CLI commands:
- Created `CafeDatabaseSG` security group with an inbound rule allowing MySQL traffic (port 3306) only from the café application server
- Designed and created two private subnets in different Availability Zones using CIDR blocks that didn't overlap with existing subnets (10.200.2.0/23 and 10.200.10.0/23)
- Created a DB subnet group that spanned both Availability Zones for high availability
- Carefully planned IP address ranges to avoid conflicts within the VPC

Nothing fancy, just solid network architecture executed through the terminal.

**Figure 3: Security group creation via AWS CLI**

[ <img width="883" height="306" alt="image" src="https://github.com/user-attachments/assets/56647a0b-534a-43cd-93b0-6620e0fa3495" />


**Figure 4: Private subnets and DB subnet group configured**


### The Main Event: Provisioning the RDS Instance

With all prerequisites in place, I executed the `aws rds create-db-instance` command with specific parameters: MariaDB 10.5.13, db.t3.micro instance class, 20GB storage, deployed in the same AZ as the café instance, secured with the security group I created, and configured with master credentials.

The instance took about 10 minutes to provision. I monitored its status using `aws rds describe-db-instances`, watching it transition from "creating" to "modifying" to "backing-up" and finally to "available." When it was ready, I captured the endpoint address—my new database's connection string.

**Figure 5: RDS instance provisioning command and initial status**

<img width="930" height="115" alt="image" src="https://github.com/user-attachments/assets/ee8f90e6-30eb-4fcc-a549-a95bedd4ec34" />

**Figure 6: RDS instance status showing "available"**

![RDS Available Screenshot](./images/rds-available.png)
<!-- Upload to: repository_root/images/rds-available.png -->

### The Critical Part: Database Migration

This was the moment of truth. I connected to the CafeInstance (the application server) and used `mysqldump` to create a complete backup of the local `cafe_db` database. The backup file contained all the SQL statements needed to recreate the schema and data.

Then I restored the backup to the RDS instance using the `mysql` command, pointing it at the RDS endpoint. The restoration completed successfully—all tables, indexes, and customer orders transferred intact.

**Figure 7: mysqldump backup creation and restoration to RDS**

![Database Migration Screenshot](./images/database-migration.png)
<!-- Upload to: repository_root/images/database-migration.png -->

**Figure 8: Verification query showing migrated data**

![Migration Verification Screenshot](./images/migration-verification.png)
<!-- Upload to: repository_root/images/migration-verification.png -->

### The Switchover: Reconfiguring the Application

Rather than hardcoding database connections (bad practice), the café application used AWS Systems Manager Parameter Store. I simply updated the `/cafe/dbUrl` parameter to point to the RDS endpoint instead of localhost. One parameter change, and the entire application seamlessly switched to the managed database.

**Figure 9: Parameter Store update with new RDS endpoint**

![Parameter Store Screenshot](./images/parameter-store-update.png)
<!-- Upload to: repository_root/images/parameter-store-update.png -->

### The Moment of Truth: Testing and Verification

I accessed the café website and navigated to the Order History page. All my original orders were there—the migration was successful. I placed a few new orders to confirm the application could write to the RDS database. Everything worked perfectly.

**Figure 10: Café website working with RDS database**

![Website Working Screenshot](./images/website-working.png)
<!-- Upload to: repository_root/images/website-working.png -->

### Monitoring: CloudWatch Metrics in Action

Finally, I explored the monitoring capabilities. I opened an interactive MySQL session from the CafeInstance and watched the DatabaseConnections metric in the RDS console. The CloudWatch graph showed exactly 1 connection active. When I closed the session, the metric dropped back to 0. Seeing infrastructure monitoring in real-time was incredibly satisfying.

**Figure 11: CloudWatch metrics showing database connections**

![CloudWatch Monitoring Screenshot](./images/cloudwatch-monitoring.png)
<!-- Upload to: repository_root/images/cloudwatch-monitoring.png -->

---

## What I Learned

This wasn't just about moving a database. The real value was in:

- **Database Migration Strategy** - I experienced firsthand how to safely migrate production data using backup and restore techniques without application downtime
- **AWS Networking Fundamentals** - I gained deep understanding of VPCs, subnets, CIDR blocks, security groups, and how they enable secure multi-tier architectures
- **Infrastructure as Code** - I learned to build complex AWS infrastructure entirely through the CLI, understanding every component and connection
- **Managed Services Benefits** - I saw how RDS provides automated backups, monitoring, and high availability without managing the underlying infrastructure

It's one thing to click through a console wizard. It's another to architect and build the entire infrastructure programmatically, understanding every networking decision and security boundary.

---

## Repository Contents

```
.
├── images/                           # Screenshots documenting the process
│   ├── aws-banner.png
│   ├── cafe-orders.png
│   ├── cli-configuration.png
│   ├── security-group-creation.png
│   ├── subnets-creation.png
│   ├── rds-creation.png
│   ├── rds-available.png
│   ├── database-migration.png
│   ├── migration-verification.png
│   ├── parameter-store-update.png
│   ├── website-working.png
│   └── cloudwatch-monitoring.png
├── architecture-diagrams/            # Before and after architecture
│   ├── starting-architecture.png
│   └── final-architecture.png
├── cli-commands.md                   # Reference of all CLI commands used
└── README.md                         # You're reading it
```

---

## Want to Try This Yourself?

If you have access to AWS and want to replicate this:

1. Launch an EC2 instance with a local MySQL/MariaDB database
2. Use the AWS CLI to create RDS prerequisites (security groups, subnets, DB subnet group)
3. Provision an RDS instance with appropriate settings for your use case
4. Use mysqldump to backup your local database
5. Restore the backup to RDS using the mysql client
6. Update your application's database connection string
7. Test thoroughly and monitor using CloudWatch

It's a complex exercise, but it builds real cloud migration and networking muscle.

---

## Tech Stack

- **Cloud Platform:** AWS (EC2, RDS, VPC, Systems Manager, CloudWatch)
- **Database:** MariaDB 10.5.13
- **Tools:** AWS CLI, mysqldump, mysql client, EC2 Instance Connect
- **Architecture:** Multi-tier application with private database subnet

---

## Key Commands Used

```bash
# Create security group
aws ec2 create-security-group --group-name CafeDatabaseSG

# Create private subnets
aws ec2 create-subnet --vpc-id <VPC_ID> --cidr-block 10.200.2.0/23

# Create DB subnet group
aws rds create-db-subnet-group --db-subnet-group-name "CafeDB Subnet Group"

# Create RDS instance
aws rds create-db-instance --db-instance-identifier CafeDBInstance

# Backup local database
mysqldump --user=root --databases cafe_db > cafedb-backup.sql

# Restore to RDS
mysql --user=root --host=<RDS_ENDPOINT> < cafedb-backup.sql
```

---

*Completed as part of AWS Training & Certification Challenge Lab*

![Footer](./images/footer.png)
<!-- Upload to: repository_root/images/footer.png -->
