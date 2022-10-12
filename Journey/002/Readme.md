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

- ### Memory Optimized
  - Fast performance for workloads that process large data sets in memory.
  - Use Cases:
    - High performance, relational/non relational databases
    - Distributed web scale cache stores
    - In - memory databases optimized for BI(Business Intelligence)
    - Applications performing real-time processing of big structured data.
  - R Series EC2