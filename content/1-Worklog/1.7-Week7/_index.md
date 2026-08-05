---
title: "Week 7 Worklog"
date: 2026-08-03
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

### Week 7 Objectives:

- Deploy monitoring and health check features for the **Automatic Image Optimization System on AWS**.
- Research how to use Amazon CloudWatch to monitor AWS Lambda.
- Verify access permissions and security configurations for AWS resources within the system.

### Tasks to be implemented this week:

| Day | Tasks                                                                                                                                                                                           | Start Date | End Date   | Documentation Source                      |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | ---------- | ----------------------------------------- |
| Mon | - Research Amazon CloudWatch for system monitoring <br> - Check Lambda logs: <br>&emsp; + Execution log <br>&emsp; + Error log <br>&emsp; + Runtime information                                 | 03/08/2026 | 03/08/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Tue | - Monitor AWS Lambda operations after image processing <br> - Verify key metrics: <br>&emsp; + Lambda invocation <br>&emsp; + Execution time <br>&emsp; + Error message                         | 04/08/2026 | 04/08/2026 | -                                         |
| Wed | - Research Amazon SNS for system notifications <br> - Learn how to integrate SNS with other AWS services when events or errors occur                                                            | 05/08/2026 | 05/08/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Thu | - Verify and update IAM permissions for the system <br> - Check access permissions between components: <br>&emsp; + Lambda → S3 <br>&emsp; + Lambda → DynamoDB <br>&emsp; + User → AWS Resource | 06/08/2026 | 06/08/2026 | -                                         |
| Fri | - Check system security configurations <br> - Research AWS KMS for data protection <br> - Re-test the entire workflow after completing monitoring and security setups                           | 07/08/2026 | 08/08/2026 | -                                         |

### Results achieved in Week 7:

- Understood the role of Amazon CloudWatch in monitoring AWS systems.

- Acquired the ability to inspect and analyze Lambda logs:
  - Track Lambda trigger execution process.
  - Inspect execution details.
  - Detect and analyze errors during processing.

- Verified system operational status through key metrics:
  - Lambda invocation.
  - Execution time.
  - Error message.

- Researched how to use Amazon SNS to support sending notifications when system events or errors occur.

- Verified and adjusted IAM access permissions for system components:
  - AWS Lambda has permissions to read and write data on Amazon S3.
  - AWS Lambda has permissions to store metadata in Amazon DynamoDB.
  - Ensured AWS resources are accessed according to their intended usage.

- Learned data security mechanisms using AWS KMS.

- Completed monitoring and security checks, enabling better operational tracking, error detection, and resource access management for the system.
