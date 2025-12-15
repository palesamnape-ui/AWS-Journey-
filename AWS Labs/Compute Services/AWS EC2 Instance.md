# Introduction to Amazon EC2 – Challenge Lab

## Overview

This repository documents my completion of the **Introduction to Amazon EC2** lab. In this lab, I gained hands-on experience launching, managing, monitoring, resizing, and terminating an Amazon EC2 instance using the AWS Management Console.

Through a guided, real-world scenario, I worked with a live EC2 instance to understand how compute resources are provisioned, secured, monitored, and scaled in the AWS Cloud.

*(Figure 1: High-level architectural diagram of the EC2 web server deployment.)*

<img width="1183" height="589" alt="ec2 1 1" src="https://github.com/user-attachments/assets/50036a5e-792f-490b-88e6-2f1720acb343" />



## The Challenge Objectives

By the end of this lab, I successfully completed the following objectives:

1. Launch an Amazon EC2 instance with termination protection enabled.
2. Monitor the EC2 instance using status checks and CloudWatch metrics.
3. Modify a security group to allow HTTP access to a web server.
4. Resize the EC2 instance and its EBS root volume.
5. Test termination protection and safely terminate the instance.

---

## ⚙️ Execution Step-by-Step

### Step 1: Launching the EC2 Instance

I began by accessing the AWS Management Console through the lab environment. Once the lab status indicated that resources were ready, I navigated to the **EC2 Dashboard** and launched a new instance.

Key configuration choices included:

* **Instance Name:** Web Server
* **AMI:** Amazon Linux 2023 (default)
* **Instance Type:** t3.micro
* **Key Pair:** Proceeded without a key pair (not required for this lab)
* **VPC:** Lab VPC
* **Security Group:** Custom security group with no inbound rules initially
* **Storage:** Default 8 GiB EBS root volume
* **Termination Protection:** Enabled

I also configured **User Data** to automatically install and start an Apache web server and deploy a simple HTML page on launch.

*(Figure 2: EC2 instance launch configuration and user data script.)*

<img width="1318" height="671" alt="ec2 2" src="https://github.com/user-attachments/assets/4d6598dc-6b58-43e3-a0ea-8ff2f68d10fb" />


<img width="1273" height="542" alt="ec2 succes" src="https://github.com/user-attachments/assets/3ce229cb-6a8c-4e07-9468-6341ad3cfb7d" />



After launching, I verified that the instance reached a **Running** state and passed both system and instance status checks.

---

### Step 2: Monitoring the EC2 Instance

With the instance running, I explored different monitoring capabilities provided by AWS.

I reviewed:

* **Status Checks:** Confirmed that both system reachability and instance reachability checks passed.
* **Monitoring Tab:** Observed Amazon CloudWatch metrics such as CPU utilization.
* **Instance Screenshot:** Captured a console screenshot to simulate troubleshooting scenarios when SSH or RDP access is unavailable.

*(Figure 3: EC2 status checks and CloudWatch monitoring metrics.)*

<img width="1359" height="618" alt="ec2 sucess2" src="https://github.com/user-attachments/assets/b997a1d3-07ea-487c-ae25-fbe7ab6212f5" />



This step reinforced the importance of proactive monitoring to maintain availability and reliability.

---

### Step 3: Updating the Security Group and Accessing the Web Server

Initially, I attempted to access the web server using the instance’s **Public IPv4 address**, but the request failed. This occurred because inbound HTTP traffic (port 80) was not permitted by the security group.

To resolve this, I:

* Navigated to **Security Groups** under Network & Security.
* Edited the inbound rules for the Web Server security group.
* Added an **HTTP rule (port 80)** with a source of **Anywhere (IPv4)**.

After saving the rule and refreshing the browser, the web page displayed the expected message:

**“Hello From Your Web Server!”**

*(Figure 4: Successful access to the web server after updating security group rules.)*

<img width="835" height="408" alt="image" src="https://github.com/user-attachments/assets/be614289-7a11-4871-b313-165fe1448fda" />


This task clearly demonstrated how security groups function as virtual firewalls in AWS.

---

### Step 4: Resizing the EC2 Instance and EBS Volume

To simulate scaling, I resized both the compute and storage resources.

First, I stopped the instance and changed:

* **Instance Type:** From t3.micro to t3.small

Next, I modified the attached EBS root volume:

* **Disk Size:** Increased from 8 GiB to 10 GiB

Once the changes were applied, I restarted the instance and confirmed that it was running with the updated resources.

*(Figure 5: Instance type and EBS volume modification.)*

> **[Insert instance resize and volume modification screenshot here]**

---

### Step 5: Testing Termination Protection

To validate termination protection, I attempted to terminate the instance while protection was enabled. AWS correctly prevented the termination and displayed an error message.

I then:

* Disabled termination protection.
* Successfully terminated the EC2 instance.

This confirmed my understanding of how termination protection helps prevent accidental resource deletion.

*(Figure 6: Termination protection test and successful instance termination.)*

> **[Insert termination protection error and termination screenshot here]**

---

## Key Takeaways

Completing this lab strengthened my understanding of:

* **EC2 Lifecycle Management:** Launching, stopping, resizing, and terminating instances.
* **Security Groups:** Using inbound rules to control network access.
* **Monitoring & Troubleshooting:** Leveraging status checks, CloudWatch metrics, and instance screenshots.
* **Scalability:** Adjusting compute and storage resources to meet workload demands.
* **Cost & Safety Controls:** Using termination protection to avoid accidental deletions.

---

*This project was completed as part of an AWS Training & Certification hands-on lab.*
