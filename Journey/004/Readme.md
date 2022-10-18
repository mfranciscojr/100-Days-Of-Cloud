# Day 004 - EC2 Instance Storage
## Introduction

Goal: Learn EC2 Instance Storage to further add knowledge about AWS Services to help me in my certification.

## What is an EBS Volume
- An EBS(elastic block store) Volume is a network drive that you can attach to your EC2 Instance while they run.
- It allows your instances to persist data, even after their termination.
- They can only be mounted to one instance at a time(Cloud Practitioner Level).
- They are bound to a specific availability zone.

## EBS Volume
- It's a network drive(i.e not a physical drive)
  - It uses the network to communicate the instace, which means there might be a bit of latency.
  - It can detached from EC2 instance and attached to another one quickly
- It's locked to an AZ.
  - An EBS volume on us-east-1 cannot be attached to us-east-2
  - To move a volume accross, you first need to snapshot it.
- Have a provisioned capacity (size in GB's and IOPS)
  - You get billed for all the provisioned capacity
  - You can increase the capacity of the drive over-time

## EBS Snapshot
- Make backup(Snapshot) of your EBS volume at a point in time
- Not necessary to detach volume to do snapshot, but recommended
- Can copy snapshots accross AZ or Region

## EBS Snapshots Features
- EBS Snapshot Archieve
  - Move a snapshot to an archive tier that is 75% cheaper
  - Takes within 24 to 72 hours for restoring the archive
- Recycle Bin for EBS Snapshots
  - Setup rules to retain deleted snapshots so you can recover them after an accidental deletion.
  - Specify retention(from 1 day to 1 year)

## AMI Overview
- AMI = Amazon Machine Image
- AMI are customization of an EC2 instance
  - You can add your own software, configuration, operating system, monitoring.....
  -  Faster boot / configuration time because all your software is pre-packaged
-  AMI are built for specific region(and can be copied across regions)
-  You can launch EC2 instances from:
  -   A Public AMI: AWS provided
  -   Your own AMI: you make and maintain them yourself
  -   An AWS Marketplace AMI: an AMI someone else made(and potentially sells)

## AMI Process(from an EC2 Instance)
- Start an EC2 Instance and customize it
- Stop the instance(for data integrity)
- Build an AMI - this will also create and EBS Snapshot
- Launch the instace from the customized AMI

## EC2 Image Builder
- Used to automate the creation of Virtual Machine or container images
- Automate the creation, maintain, validate and test EC2 AMIs
- Can be run on a schedule (weekly, or whenever packages are updated, etc etc)
- Free service (only pay the underlying resources)

## EC2 Instance Store
- EBS volumes are network drives with good but limited performance
- If you need a high-performance hardware disk, use EC2 instance store
- Better I/O performance, very high IOPS
- EC2 Instance sore lose their storage if they're stopped(ephemeral)
- Good for buffer/cache/scratch data/ temporary content
- Risk of data loss if hardware fails
- Backups and replication are customer responsibility.

## EFS - Elastic File System
- Managed NFS(network file system) that can be mounted on multiple instances
- EFS works with Linux EC2 Instance in multi-az
- High available,scalable, expensive(3x gp2 ebs), pay per use, no capacity planning

## EFS Infrequent(EFS-IA)
- Storage class that is cost-optimized for files not accessed everyday
- Up to 92% lower cost compared to EFS Standard
- EFS will automatically move your files to EFS-IA based on last time they were accessed
- Enable EFS-IA with a lifecycle policy
- Transparent to the application

## Shared Responsibily for EC2 Storage
- AWS
  - Infrastructure
  - Replication for data for EBS Volume and EFS drives
  - Replacing faulty hardware
  - Ensuring their employees cannot access your data
 - Customer
  - Setting up backup/snapshot procedures
  - Setting up data encryption
  -  Responsibility of any data on the drive
  -  Understanding the risk of using EC2 Instance Store
  
## Amazon FSx - Overview
- launch 3rd party high-performance file systems on AWS
- Fully Managed Service
  - FSx for lustre
  - FSx for windows file server
  - FSx for NetApp onTAP

### FSx for Windows File Server
- A fully managed, higly reliable and scalabe Windows native shared file system
- Built on windows file server
- Supports SMB protocol and NTFS
- Integrated with Microsoft Active Directory
- Can be access from AWS or your on-premise infratructure

### FSx for Lustre
- A fully managed high-performance, scalable file storage for High-Performance Computing(HPC)
- The name Lustre is derived from Linux and Cluster
- Machine Learning, Analytics, Video Processing, Financial Modelling
- Scales up to 100s GB/s, millions of IOPS, sub-ms latencies.
