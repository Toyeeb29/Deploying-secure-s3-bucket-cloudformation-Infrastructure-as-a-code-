# Deploying-secure-s3-bucket-cloudformation-Infrastructure-as-a-code-
# What is AWS CloudFormation?
AWS CloudFormation is a service that lets you build and manage AWS resources through code instead of manual setup in the console. You create a YAML template that outlines the infrastructure you need like a secure S3 bucket and CloudFormation automatically provisions everything for you. This follows the principles of Infrastructure as Code (IaC), ensuring your cloud environment is deployed securely and automatically.
# Overview
This project explains how to deploy a CloudFormation template using the AWS CLI to create a secure Amazon S3 bucket. The bucket is configured to block all public access and uses AES-256 server-side encryption to protect stored data.
# Prerequisites for the project
Ensure you have:
An AWS account
AWS CLI installed on your operating system
AWS CLI configured (run the command aws configure in your OS terminal and enter your credentials)

# Steps to Deploy the CloudFormation Template
1. Create the CloudFormation Template
Create a new YAML file called: secure-s3-bucket.yml. Copy and paste in the following into your file:
AWSTemplateFormatVersion: 2010-09-09
Description: Secure S3 Bucket Example

Resources:
  SecureBucket:
    Type: AWS::S3::Bucket
    Properties:
      BucketName: my-secure-bucket-atand-2026-v1
      PublicAccessBlockConfiguration:
        BlockPublicAcls: true
        BlockPublicPolicy: true
        IgnorePublicAcls: true
        RestrictPublicBuckets: true
      BucketEncryption:
        ServerSideEncryptionConfiguration:
          - ServerSideEncryptionByDefault:
              SSEAlgorithm: AES256

# Create the CloudFormtion stack using AWS CLI
Run this in your windows terminal:
aws cloudformation deploy --template-file secure-s3-bucket.yml --stack-name my-secure-bucket-atand-2026-v1 --capabilities CAPABILITY_NAMED_IAM

# Note:
Make sure the bucket name is globally unique. If my-secure-bucket-atand-2026-v1 is already taken, change the bucket name in the YAML file.
For "--template file", make sure to specify the correct path where your template file is located in your local system.

# 3. Monitor Stack Creation
Status will update in your terminal as shown below:
<img width="611" height="53" alt="cli s3 creation" src="https://github.com/user-attachments/assets/8b09d449-118f-43b8-b5bd-bbb2765b6496" />

You can also verify by going ro CloudFormation in the AWS Console to view the stack status:
<img width="845" height="220" alt="console final" src="https://github.com/user-attachments/assets/a7281c2e-6080-44e6-ade4-e52b0add2b37" />



    
