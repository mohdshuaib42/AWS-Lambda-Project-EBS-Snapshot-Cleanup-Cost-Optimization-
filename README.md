# 📦 AWS Lambda Project: EBS Snapshot Cleanup (Cost Optimization)

## 🚀 Overview

This project demonstrates how to use AWS Lambda to automatically identify and delete unused EBS snapshots, helping reduce unnecessary storage costs in your AWS account.

## 🎯 Problem Statement

Over time, EBS snapshots accumulate in your AWS account. Many of these snapshots are no longer associated with active EC2 instances, leading to:

💸 Increased storage costs </br>
🗂️ Resource clutter </br>
⚠️ Inefficient cloud resource management

## 💡 Solution

We created an AWS Lambda function that: </br>

Fetches all EBS snapshots owned by the account </br>
Retrieves all active EC2 instances (running + stopped) </br>
Checks whether snapshots are associated with active volumes </br>
Deletes unused (stale) snapshots automatically

## 🏗️ Architecture
AWS Lambda (Python + Boto3) </br>
        ↓ </br>
Fetch EBS Snapshots </br>
        ↓ </br>
Fetch EC2 Instances </br>
        ↓ </br>
Compare Snapshot ↔ Volume ↔ Instance </br>
        ↓ </br>
Delete Unused Snapshots 

## 🧠 How It Works
Uses Boto3 (AWS SDK for Python) </br>
Calls: </br>
describe_snapshots() </br>
describe_instances() </br>
Maintains a list of active instance IDs </br>
Iterates through snapshots and deletes those: </br>
Not linked to any active volume </br>
OR whose volume no longer exists

## 🛠️ Tech Stack
AWS Lambda </br>
Python 3.x </br>
Boto3 </br>
AWS EC2 / EBS </br>
IAM Roles & Policies

## 🔐 IAM Permissions Required
</br>
Attach a role with the following permissions:

```json 
{
  "Effect": "Allow",
  "Action": [
    "ec2:DescribeSnapshots",
    "ec2:DescribeInstances",
    "ec2:DeleteSnapshot"
  ],
  "Resource": "*"
}
```
</br>
# 👨‍💻 Author

## Mohd Shuaib
🚀 DevOps & Cloud Enthusiast
