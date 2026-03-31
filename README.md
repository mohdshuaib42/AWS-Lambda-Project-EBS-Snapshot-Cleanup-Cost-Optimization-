# 📦 AWS Lambda Project: EBS Snapshot Cleanup (Cost Optimization)

## 🚀 Overview

This project demonstrates how to use AWS Lambda to automatically identify and delete unused EBS snapshots, helping reduce unnecessary storage costs in your AWS account.

## 🎯 Problem Statement

Over time, EBS snapshots accumulate in your AWS account. Many of these snapshots are no longer associated with active EC2 instances, leading to:

💸 Increased storage costs
🗂️ Resource clutter
⚠️ Inefficient cloud resource management

## 💡 Solution

We created an AWS Lambda function that:

Fetches all EBS snapshots owned by the account
Retrieves all active EC2 instances (running + stopped)
Checks whether snapshots are associated with active volumes
Deletes unused (stale) snapshots automatically

## 🏗️ Architecture
AWS Lambda (Python + Boto3)
        ↓
Fetch EBS Snapshots
        ↓
Fetch EC2 Instances
        ↓
Compare Snapshot ↔ Volume ↔ Instance
        ↓
Delete Unused Snapshots

## 🧠 How It Works
Uses Boto3 (AWS SDK for Python)
Calls:
describe_snapshots()
describe_instances()
Maintains a list of active instance IDs
Iterates through snapshots and deletes those:
Not linked to any active volume
OR whose volume no longer exists

## 🛠️ Tech Stack
AWS Lambda
Python 3.x
Boto3
AWS EC2 / EBS
IAM Roles & Policies

## 🔐 IAM Permissions Required

Attach a role with the following permissions:

{
  "Effect": "Allow",
  "Action": [
    "ec2:DescribeSnapshots",
    "ec2:DescribeInstances",
    "ec2:DeleteSnapshot"
  ],
  "Resource": "*"
}

# 👨‍💻 Author

## Mohd Shuaib
🚀 DevOps & Cloud Enthusiast