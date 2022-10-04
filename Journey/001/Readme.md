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
![Lab](https://github.com/mfranciscojr/100-Days-Of-Cloud/blob/main/images/100daysofcloud-day001.gif)
[![Youtube](https://img.youtube.com/vi/tHoDYWbYgxk/0.jpg)](https://youtu.be/tHoDYWbYgxk)

### :computer: Hands on Lab - IAM Users and Groups via CLI
Required:

- Create a user account for Summer and Arthas
- Create two groups, S3 with full access and RDS with Read Only Privilege
- Assign Summer to S3 groups with progmatic access
- Assign Arthas to RDS without progmatic access

#### CLI Lab Solution

[![Youtube](https://img.youtube.com/vi/tHoDYWbYgxk/0.jpg)](https://youtu.be/6qWyGZQ7S6o)

