![Security-Groups](https://github.com/mfranciscojr/100-Days-Of-Cloud/blob/094037b70e2b25f9516ce67f35a092c5861543cf/images/Day003/aws_security_groups.png)

# Day 003 - Security Groups

## Introduction

Goal: Learn Security Groups to further add knowledge about AWS Services to help me in my certification.

## Introduction to Security Groups
- Security groups are the fundamental of network security in AWS.
- They control how traffic is allowed into or out of EC2 Instances.
- Security groups only contain allow rules.
- Security groups can reference by IP or by security groups.
- Security groups are acting as a "firewall" on EC2 instances
- They regulate
  - access to ports
  - authorized ip ranges - ipv4 and ipv6
  - control of inbound network (from other to the instance)
  - control of outbound network (from instance to other)

## Good to know
- Can be attached to multiple instances
- Locked down to a region/VPC combination
- Does live "outside" the EC2 - if traffic is blocked the EC2 instance wont see it.
- It's good to maintain one seperate security group for ssh access
- If your application gives "connection refused" error, then it's an application error or it's not launched
- All inbound traffic  is blocked by default.
- All outbound traffic is allowed by default.

## Classic ports need to know
- 22 = ssh (secure shell) - log into linux instance for management.
- 21 = ftp (file transfer protocol) - transfer files into a file share.
- 22 = sftp (secure file transfer protocol) secure file transfer to a file share using ssh.
- 80 = http - access to unsecured websites
- 443 = https - access to secure websites using ssl
- 3389 = rdp (remote desktop protocol) - log into windows instance