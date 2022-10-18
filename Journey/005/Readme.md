# Day 005 - AWS Elastic Load Balancing and Auto-Scaling Groups
## Introduction

Goal: Learn AWS ELB and ASG to further add knowledge about AWS Services to help me in my certification.

## What is Scalability and High Availability
- Scalability means that an application / system can handle greater loads by adapting.
- There are two kinds of scalability.
  - Vertical Scalability
  - Horizontal Scalability (elasticity)
- Scalability is linked but different to High Availability.

## Vertical Scalability
- Vertical scalability means increasing the size of the instance.
- for example:
   - application runs on t2.micro
   - scaling that application / system vertically means running it on a t2.large
- Vertical scalability is very common for non distributed system like databases.
- There's usually a limit on how much you can vertically scale.

## Horizontal Scalability
- Horizontal scalability means increasing the number of instances / system for your application
- Horizontal scaling implies distributed systems. 
- This is very common for web application and modern applications.
- It's easy to horizontally scale thanks to the cloud offerings such as Amazon EC2.
  
## High Availability
- High Availability usually goes hand in hand with horizontal scaling
- High availability means running your application / system in at least 2 availability zones.
- The goal of high availability is to survive a data center loss(disaster)

## High Availability and Scalability for EC2
- Vertical: increase instance size(=scale up / down)
  - from t2.nano - to u-l2tbl.metal - may change
- Horizontal: Increase the number of instances(scale out/ in)
  - Auto-Scaling Group
  - Load Balancer
- High-Availability
  - Auto-Scaling Group Multi-AZ
  - Load-Balancer Multi-AZ

## Scalability vs Elasticity(Agility)
- Scalability = ability to accomodate a larger load by making the hardware stronger(scale up) or by adding nodes/instance(scale out)
- Elasticity = once a system is scalable, elasticity means that there will be some "auto-scaling so that the system can scale based on the load. This is "cloud-friendly": pay-per-use, match demand, optimize costs.
- Agility = (not related to scalability-distractor) new IT resources are only a click away, which means that you can reduce the time to make those resources available to your developers from weeks to just minutes.

---

## Elastic Load Balancing

### What is load-balancing?
- Load Balancers are servers that forwards network traffic to multiple servers/instances downstream.

### Why use load-balancer
- Spread accross multiple downstream instances
- Expose a single point of access(DNS) to your application
- Seamlessly handle failures for downstream instances
- Do regular health checks to your instances
- Provide SSL termination(https) for your websites
- High Availability accross zones
  
## Why use an Elastic Load Balancer
- An ELB(Elastic Load Balancer) is a managed load balancer by AWS
  - AWS guarantess that it will be working
  - AWS takes care of upgrades, maintenance, high-availability.
  - AWS provides only a few configuration knobs.
- It cost less to setup your own load balancer but it will be a lot more effort on your end(maintenance, integrations)
- 4 kinds of load balancers
  - Application Load balancers(HTTP/HTTPS only) - Layer 7
  - Network Load-Balancers(ultra high performance, allows for TCP) layer 4
  - Classic Load Balancer(slowly retiring) - layer 4 and 7
  - Gateway Load Balancer (new)