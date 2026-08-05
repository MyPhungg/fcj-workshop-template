---
title: "Week 4 Worklog"
date: 2026-07-13
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

### Week 4 Objectives:

- Deploy primary storage and processing components for the **Automatic Image Optimization System on AWS**.
- Configure Amazon S3 for storing input and output images.
- Build an AWS Lambda Function to execute automated image optimization.

### Tasks to be implemented this week:

| Day | Tasks                                                                                                                                                                                         | Start Date | End Date   | Documentation Source                      |
| --- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | ---------- | ----------------------------------------- |
| Mon | - Create and configure Amazon S3 Buckets for the system <br>&emsp; + Input image storage bucket <br>&emsp; + Processed image storage bucket <br> - Verify Object storage structure in S3      | 13/07/2026 | 13/07/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Tue | - Research S3 Event Trigger mechanisms <br> - Configure event triggers when new images are uploaded to S3 <br> - Connect S3 to AWS Lambda Function                                            | 14/07/2026 | 14/07/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Wed | - Deploy AWS Lambda Function for image processing <br> - Configure Python Lambda Runtime <br> - Set up Environment Variables for the Lambda Function <br> - Verify Lambda Execution Role      | 15/07/2026 | 15/07/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Thu | - Build image processing logic using Python Pillow <br>&emsp; + Read images from S3 <br>&emsp; + Resize images <br>&emsp; + Optimize image file size <br>&emsp; + Save processed images to S3 | 16/07/2026 | 16/07/2026 | -                                         |
| Fri | - Test automated image processing workflow <br>&emsp; + Upload images to S3 <br>&emsp; + Verify Lambda trigger execution <br>&emsp; + Verify successful storage of optimized images           | 17/07/2026 | 18/07/2026 | -                                         |

### Results achieved in Week 4:

- Successfully deployed Amazon S3 resources serving the system:
  - Input image storage bucket.
  - Optimized output image storage bucket.

- Configured S3 Event Triggers to automatically trigger Lambda upon new image uploads.

- Successfully deployed the image processing AWS Lambda Function:
  - Configured Python Runtime.
  - Configured access permissions via IAM Role.
  - Set up environment variables supporting the processing workflow.

- Built image processing functionality using Python Pillow:
  - Read image files from S3.
  - Performed image resizing based on configured dimensions.
  - Optimized image file size.
  - Uploaded processed images to S3.

- Successfully tested the core workflow:
  - User uploads an image to S3.
  - S3 generates an event.
  - Lambda gets triggered.
  - Processed image is stored in the S3 Output Bucket.

- Completed core system processing logic, establishing a baseline to build metadata storage and processing tracking features in subsequent weeks.
