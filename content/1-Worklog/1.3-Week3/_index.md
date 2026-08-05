---
title: "Week 3 Worklog"
date: 2026-07-06
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

### Week 3 Objectives:

- Analyze requirements and design the architecture for the **Automatic Image Optimization System on AWS**.
- Define the role of each AWS service used in the system.
- Prepare necessary components prior to system deployment.

### Tasks to be implemented this week:

| Day | Tasks                                                                                                                                                                                                                                                                 | Start Date | End Date   | Documentation Source                      |
| --- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | ---------- | ----------------------------------------- |
| Mon | - Analyze requirements for the Automatic Image Optimization System <br> - Identify key system objectives: <br>&emsp; + Receive user images <br>&emsp; + Automatically optimize images <br>&emsp; + Store post-processing images <br>&emsp; + Track processing details | 06/07/2026 | 06/07/2026 | -                                         |
| Tue | - Design overall system architecture <br> - Build processing workflow: <br>&emsp; User Upload Image <br>&emsp; → Amazon S3 <br>&emsp; → AWS Lambda <br>&emsp; → Output Storage <br>&emsp; → DynamoDB Metadata                                                         | 07/07/2026 | 07/07/2026 | -                                         |
| Wed | - Research the roles of AWS services in the system: <br>&emsp; + Amazon S3 <br>&emsp; + AWS Lambda <br>&emsp; + Amazon DynamoDB <br>&emsp; + Amazon CloudWatch <br>&emsp; + Amazon SNS <br>&emsp; + IAM <br>&emsp; + AWS KMS                                          | 08/07/2026 | 08/07/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Thu | - Design image processing workflow: <br>&emsp; + Upload images to the system <br>&emsp; + Trigger Lambda via S3 Event Trigger <br>&emsp; + Process and optimize images <br>&emsp; + Save output images and metadata                                                   | 09/07/2026 | 09/07/2026 | -                                         |
| Fri | - Prepare deployment environment for the system <br> - Verify AWS access permissions <br> - Identify AWS resources required for development                                                                                                                           | 10/07/2026 | 11/07/2026 | -                                         |

### Results achieved in Week 3:

- Analyzed requirements for the **Automatic Image Optimization System on AWS**.

- Finalized overall system architecture:
  - User uploads images to the system.
  - Images are stored on Amazon S3.
  - AWS Lambda is triggered to execute image processing.
  - Optimized output images are stored back on S3.
  - Processing metadata is stored in Amazon DynamoDB.

- Defined the role of each AWS service:
  - **Amazon S3:**
    - Stores input images.
    - Stores post-optimization images.

  - **AWS Lambda:**
    - Executes automated image processing upon upload events.

  - **Amazon DynamoDB:**
    - Stores image metadata details.
    - Tracks processing status.

  - **Amazon CloudWatch:**
    - Monitors Lambda logs and activity.

  - **Amazon SNS:**
    - Sends notifications when events or errors occur.

  - **IAM and AWS KMS:**
    - Manages resource access permissions and security.

- Built the primary processing workflow, serving as the foundation for deploying AWS components in subsequent weeks.

- Prepared the deployment environment and development plan.
