![placeholder image](https://github.com/mfranciscojr/100-Days-Of-Cloud/blob/b09b56dea78bc5e78a4f240e92ab815d844c90aa/images/Day002/day002.png)

# Day 002 - EC2

## Introduction

Goal: Learn EC2 to further add knowledge about AWS Services to help me in my certification.

## Prerequisite

- Basic understanding on how EC2 services works.

## Use Case

- Deploying servers and services on AWS using EC2 instances.

## What is AWS EC2

- EC2 is one of the most popular of AWS service offering.
- EC2 = Elastic Compute Cloud = Infrastructure As A Service (IAAS)
- It mainly consists in the capability of:
  - Renting virtual machine(EC2).
  - Storing data on virtual drives(EBS or Elastic Block Storage).
  - Distributing load accross machine(ELB or Elastic Load Balancer).
  - Scaling the services using an auto-scaling group (ASG).
- Knowing EC2 is fundamental to understand how cloud works.

## EC2 Sizing and configuration options

- Operating System Supported
  - Linux 
  - Windows
  - Mac
- How much compute power and cores(CPU)
- How much random access memory(RAM)
- How much storage space
  - Network-Attached (EBS/EFS)
  - Hardware(EC2 Instance Store)
- Network card
  - speed of the interface
  -  Public IP address
- Firewall rules(security group)
- Bootstrap script(configure at first launch) EC2 User Data

## EC2 User Data
- It is possible to bootstrap our instances using an EC2 User Data script.
- Bootstrapping means launching commands when a machine starts.
- that script is only run once at the instance first start.
- EC2 user data is used to automate boots task such as:
  - install updates
  - install software
  - download common files from the internet
  - anything you can think of to automate
- The EC2 User Data Script runs with a root user

## EC2 Instace Types Sample

![InstanceType](https://github.com/mfranciscojr/100-Days-Of-Cloud/blob/d07c5f5b060b45f830e37b5c96f9d0f9f34be07c/images/Day002/Ec2-Instance-Type-Examples.png)

---

## Hands On Lab (AWS Management Console)
#### Task:
- Create an free tier t2.micro EC2 Instance via AWS Management console.
- Use EC2 User Data Script to update and install a web server.
```
#!/bin/bash
yum update -y
yum install -y httpd
systemctl start httpd
systemctl enable httpd
echo "<h1>Hello World from $(hostname -f)</h1>" > /var/www/html/index.html
```
- Create a security group and allow ssh and http access from the public to the EC2 instance.
- Test connectivity.
  
### Solution:
[![Youtube](https://img.youtube.com/vi/NGaRHg0VFsc/0.jpg)](https://www.youtube.com/watch?v=NGaRHg0VFsc)


## AWS EC2 Instance Type

- You can use different types of EC2 intances that are optimized for differenct use-cases(https://aws.amazon.com/ec2/instance-types)
- AWS have the following naming convention(example: m5.2xlarge)
  m: instance class
  5: generation of instance(AWS Improves them over time)
  2xlarge: size within the instance type

### EC2 Instance Types

- ### General Purpose
  - Great for diversity of workloads such as web servers or code repositories.
  - Balance between compute, memory and networking
  
![general purpose](https://github.com/mfranciscojr/100-Days-Of-Cloud/blob/acb44ff5bf9fa824cece944630a743920a352b97/images/Day002/EC2-General%20Purpose%20Optimized.png)

- ### Compute Optimed
  - Great for compute-intensive task that requires high-performance processors
  - Use Cases:
    - Batch processing workloads
    - Media transcoding
    - High Performance Web Servers
    - High Performance computing(HPC)
    - Scientific modelling and machine learning
    - Dedicated gaming servers
  
![compute-optimized](https://github.com/mfranciscojr/100-Days-Of-Cloud/blob/052097c4066526897b8e591f0683d29d091eebad/images/Day002/compute-optimized.png)

- ### Memory Optimized
  - Fast performance for workloads that process large data sets in memory.
  - Use Cases:
    - High performance, relational/non relational databases
    - Distributed web scale cache stores
    - In - memory databases optimized for BI(Business Intelligence)
    - Applications performing real-time processing of big structured data.

![Memory-optimized](https://github.com/mfranciscojr/100-Days-Of-Cloud/blob/052097c4066526897b8e591f0683d29d091eebad/images/Day002/memory-optimized.png)

- ### Storage Optimized
  - Great for storage-intensive tasks that require high, sequential read and write access to large data sets on local storage.
  - Use Cases:
    - High frequency online transaction processing (OLTP) systems.
    - Relational and NOSQL databases.
    - Cache for in-memory databases(Redis)
    - Data warehousing applications
    - Distributed file-systems

![storage-optimized](https://github.com/mfranciscojr/100-Days-Of-Cloud/blob/052097c4066526897b8e591f0683d29d091eebad/images/Day002/storage-optimized.png)

## EC2 Instances Purchasing Options
- On-Demand Instances - Short workload, predictable pricing pay by the second
- Reserved(1 and 3 years)
  - Reserved Instances - long workloads.
  - Convertible Reserved Instances - long workloads with flexible instances.
- Saving Plans ( 1 and 3 years) - commitment to an amount of usage, long workload.
- Spot Instances - short workloads, cheap, can lose instances(less reliable).
- Dedicated Hosts - book an entire physical server, control instance placement.
- Capacity reservation = reserve capacity in a specific AZ for any duration.

### EC2 on Demand
- Pay what you use:
  - Linux or Windows - billing per second, after the first minute
  - All other operating systems - billing per hour
- Has the highest cost but no upfront payment
- No long term commitment
- Recommended for short-term and un-interupted workloads, where you can't predict how the application will behave.

## EC2 Reserved Instances
- Up to 72% discount compared to On-demand (Note: the % discound changes over time)
- You reserve a specific instance attributes (instance type, region, tenancy, OS)
- Reservation Period - 1 year (+ discount) or 3 years (+++ discount)
- Payment options:
  - No upfront(+)
  - Partial upfront(++)
  - All upfront(+++)
- Reserved Instance's Scope - Regional or Zonal(reserve capacity in an AZ)
- Recommended for steady-state usage applications(database)
- You can buy and sell in the reserved instance marketplace
- Convertible Reserved Instance
  - Can change the ec2 instance type, instance family, os, scope and tenancy.
  - up to 66% discount

## EC2 Savings Plan
- Get discount based on long-term usage (up to 72% - same as Reserved Instances).
- Commit to certain type of usage($10/hour for 1 or 3 years).
- Usage beyond EC2 Savings plan is billed at the On-Demand price.
- Locked to a specific instance family and AWS region(example: M5 in US-East=1)
- Flexible accross:
  - Instance Size (example: m5.xlarge, m5.2xlarge)
  - OS (example: Linux, Windows)
  - Tenancy (Host, Dedicated, Default)

## EC2 Spot Instances
- Can get a discount of up to 90% compared to On-Demand
- Instances that you can lose at any point of time if your max price is less than the current spot price.
- The MOST cost-efficient instances in AWS.
- Useful for workloads that are resilient to failure
  - Batch jobs
  - Data Analysis
  - Image Processing
  - Any distributed workloads
- Not suitable for critical jobs or databases

## EC2 Dedicated Host
- A physical server with EC2 instance capacity fully dedicated to your use-case
- Allows you to address compliance requirements.
- Use your existing server bound software licenses(per socket, per core, per VM software)
- Purchasing Options:
  - On-Demand - pay per secound for active dedicated host
  - Reserved - 1 or 3 years(No upfront, Partial upfront, All Upfront)
- The most expensive option
- User for software that have complicated licensing model(BYOL-Bring your own licenses)

## EC2 Dedicated Instances
- Instances run on hardware that's dedicated to you.
- May share hardware with other instances on the same account.
- No control over instance placement(can move hardware after Stop/Start)
  
## EC2 Capacity Reservations
- Reserve On-Demand instances capacity in a specific AZ for any duration
- You always have access to EC2 Capacity when you need it.
- No time commitment(create/cancel anytime), no billing discounts
- Combine with regional reserved instances and savings plans to benefit from billing discounts
- You're charged at On-Demand rate whether you run instances or not.
- Suitable for short term, uninteruppted workloads that needs to be in a specific AZ.

## Which purchasing options is right for me?
- Hotel Analogy
  - On-Demand:
    - coming in and staying in resort whenever we like, we pay the full price.
  - Reserved:
    - planning ahead and if we plan to stay for a long time, we may get a good discount.
  - Savings-Plan
    - pay a certain amount per hour for certain period and stay in any room(example: VIP, Non VIP, Sea View)
  - Spot Instances
    - the hotel allows people to bid for the empty rooms and the highest bidder keeps the rooms, You can get kicked out at any time.
  - Dedicated Host
    - We book an entire building of the resort
  - Capacity Reservations
    - You book a room for a period with full price even if you don't stay in it.  

## EC2 Shared Responsibility Model

### AWS
- Infrastructure (global network security)
- Isolation on physical hosts
- Replacing faulty hardware
- Compliance Validation

### User
- Security groups rules
- Operating-System patches and updates
- Software and utilities installed on EC2 instances
- IAM roles assigned
- IAM User access management
- Data Security on instance
