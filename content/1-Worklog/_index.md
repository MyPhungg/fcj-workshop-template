---
title: "Worklog Overview"
date: 2026-08-04
weight: 1
chapter: false
pre: " <b> 1. </b> "
---

During the internship program, I completed my assignments over an **8-week** period from **June 22, 2026 to August 15, 2026**.

During this time, the completed tasks included exploring the AWS platform, studying necessary Cloud services, practicing basic AWS service deployments, and applying them to build the **Automatic Image Optimization System on AWS**.

The implementation process was divided into the following phases:

- **Phase 1:** Learn foundational AWS knowledge, get acquainted with AWS Console, AWS CLI, and core services.
- **Phase 2:** Research system architecture for automated image processing and deploy necessary AWS components.
- **Phase 3:** Build image processing logic using AWS Lambda, storage via Amazon S3, and metadata management via DynamoDB.
- **Phase 4:** Finalize monitoring, security, system testing, and prepare report documentation.

The breakdown of weekly tasks is as follows:

**Week 1:** [Learn AWS Cloud and Fundamental AWS Services](1.1-week1/)

- Get familiar with the AWS Cloud platform.
- Explore primary service categories:
  - Compute
  - Storage
  - Database
  - Networking
- Create an AWS Free Tier Account.
- Configure AWS CLI and practice AWS command line operations.

**Week 2:** [Research AWS Services for the Image Processing System](1.2-week2/)

- Learn Amazon S3:
  - Bucket
  - Object
  - Permission
  - Storage management
- Learn AWS Lambda:
  - Serverless computing
  - Function
  - Trigger
- Learn DynamoDB:
  - Table
  - Partition Key
  - Sort Key
- Research integration patterns for S3, Lambda, and DynamoDB.

**Week 3:** [Design Architecture for Automatic Image Optimization System](1.3-week3/)

- Analyze system requirements.
- Design automated image processing architecture.
- Define the roles of AWS services:
  - Amazon S3
  - AWS Lambda
  - Amazon DynamoDB
  - Amazon CloudWatch
  - Amazon SNS
  - IAM
  - AWS KMS
- Design upload, processing, and image storage workflows.

**Week 4:** [Deploy Amazon S3 and AWS Lambda for Image Processing](1.4-week4/)

- Create and configure S3 Buckets for image storage.
- Configure S3 Event Triggers for Lambda.
- Deploy Lambda Function for image processing.
- Research using Python Pillow to:
  - Resize images
  - Compress images
  - Convert image formats
- Test automated upload and image processing workflow.

**Week 5:** [Build Metadata Storage Functionality using DynamoDB](1.5-week5/)

- Design DynamoDB Table for metadata storage.
- Build storage schema:
  - Batch ID
  - Processing ID
  - File information
  - Processing status
  - Processing time
  - Compression ratio
- Connect Lambda to DynamoDB.
- Verify metadata records after image processing.

**Week 6:** [Finalize Image Optimization Functionality](1.6-week6/)

- Finalize image processing logic using Python Pillow.
- Add thumbnail generation functionality.
- Support multi-format processing:
  - JPEG
  - PNG
  - WEBP
- Calculate key metrics:
  - Original size
  - Processed size
  - Compression ratio
  - Processing time
- Test end-to-end image processing workflow.

**Week 7:** [Deploy System Monitoring and Security](1.7-week7/)

- Monitor Lambda execution logs via Amazon CloudWatch.
- Verify system processing status.
- Configure SNS to send notifications upon error occurrence.
- Audit IAM Permissions.
- Research security mechanisms:
  - IAM Role
  - KMS Encryption

**Week 8:** [Complete System and Prepare Final Report](1.8-Week8/)

- Conduct full system review for the Automatic Image Optimization System on AWS.
- Test complete workflow:
  - Upload image
  - Lambda processing
  - Save output image
  - Save metadata
- Finalize deployment documentation.
- Prepare demo materials and present final results.
