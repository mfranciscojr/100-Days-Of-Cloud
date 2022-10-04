<!-- This template removes the micro tutorial for a quicker post and removes images for a full template check out the 000-DAY-ARTICLE-LONG-TEMPLATE.MD-->

# Day 001 - AWS IAM

## Introduction

✍️ (Why) To learn AWS IAM to better understand how access and permission works on AWS.

## Use Case

- ✍️ (Show-Me) Explain in one or two sentences the use case

## Cloud Research

### IAM Users and Groups

:spiral_notepad: Notes:

IAM = Identity and Access Management. Global Service.

Root Account are created by default, should not be used or shared(best practice).

Users are people within the organization and can be grouped together.

Groups only contains user not other groups

### IAM Permissions:

:spiral_notepad: Notes:

Users and groups can be assigned JSON documents called policies.

These policies define the permission of the users

In AWS you apply the concept of least privilege access, don't give more permissions than a user needs.

### :computer: Hands on Lab - IAM Users and Groups via GUI

Required:

- Create a user account for Reid and Richer
- Create two groups, S3 with full access and RDS with Read Only Privilege
- Assign Reid to S3 groups with progmatic access
- Assign Richter to RDS without progmatic access

#### Gui Lab Solution
[![Youtube](https://img.youtube.com/vi/tHoDYWbYgxk/0.jpg)](https://youtu.be/tHoDYWbYgxk)

### :computer: Hands on Lab - IAM Users and Groups via CLI
Required:

- Create a user account for Summer and Arthas
- Create two groups, S3 with full access and RDS with Read Only Privilege
- Assign Summer to S3 groups with progmatic access
- Assign Arthas to RDS without progmatic access

#### CLI Lab Solution
[![Youtube](https://img.youtube.com/vi/tHoDYWbYgxk/0.jpg)](https://youtu.be/6qWyGZQ7S6o)

### IAM Policies Inheritance:
:spiral_notepad: Notes:

Inline Policies are policy that is only attached to a user.
All policies defined are inherited by the user if assigned to a group.
User can be a member of multiple groups thus inheriting multiple policies.

IAM Policies Structure
Consist of
- Version: policy language version always include a date
- ID: an identifier for the policy. (optional attribute)
- Statement: one or more individual statements(required attribute)
  
Statement consist of
- SID: an identifier for the statement(optional)
- Effect: whether the statement allows or denies the access(Allow,Deny)
- Principal: account/user/role which this policies applies to.
- Action: List of actions this policy allow or denies
- Resource: List of resources to which the actions applied to.
  
Reference:

![IAM Policies](https://github.com/mfranciscojr/100-Days-Of-Cloud/blob/main/images/Day001/iampolicystructure.png)

### IAM Password Policy

:spiral_notepad: Notes:

- Strong Password: higher security for the account
- In AWS, you can setup a password policy
  - set minimum password length
  - require specific character types
    - uppercase
    - lowercase
    - numbers
    - non-alphanumeric characters
- Allow all IAM users change their passwords
- Have a password expiration which users needs to change periodically.
- Prevent password re-use

### MFA (Multi Factor Authentication)

:spiral_notepad: Notes:

- Provides additional layer of protection for AWS user account by having a digital or physical authenticators.
- Best practice to use MFA for all aws accounts.
- Even if password is compromised account is still secured as the bad actor needs the MFA to login.

### How can users access AWS?

:spiral_notepad: Notes:

- To access AWS, three options are available
  - AWS management console (Password + MFA)
  - AWS Command Line Interface using access keys (CLI)
  - AWS SDK - Software Development Kit
- Access Keys are generated through the AWS Console
- Users manage their own acces keys
- Access Keys are secret, just like password. Don't share them.
  
### What is AWS CLI?

:spiral_notepad: Notes:

- A tool that enables you to interact with AWS services using commands in your command line shell/terminal.
- Direct access to the public API's oif AWS Services.
- You can develop scripts to manage your resources.
- It's open-source
- Alternative to using AWS Console


### What is AWS SDK?

:spiral_notepad: Notes:

- AWS SDK - Software development kit
- Language specific API's(set of libraries)
- Enables you to access and manage AWS Services Programmatically
- Embedded within application
- Supports
  - Javascript, Python, PHP, .NET, Ruby, Java, Go, NodeJS, C++)
  - Mobile SDK (Android, IOS)
  - IOT Device SDK (Embedded C, Arduino)

### IAM Roles for AWS Services

:spiral_notepad: Notes:

- Some AWS service will need to perform action on user's behalf.
- Common Roles:
  - EC2 Instance Roles
  - Lambda Function Roles
  - Roles for CloudFormation

### :computer: Hands on Lab - Create a IAM Role for AWS Services with READ ONLY Access for EC2 Instances to Read IAM

- Create a role named ReadOnlyEC2 for AWS Service with ReadOnly Access for EC2 Instances to view IAM Service
- Create an EC2 Instace and test the role.