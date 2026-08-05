---
title: "Week 8 Worklog"
date: 2026-08-10
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Week 8 Objectives:

- Complete the **Automatic Image Optimization System on AWS**.
- Re-verify the entire end-to-end system workflow post-deployment.
- Consolidate documentation, project results, and prepare presentation materials.

### Tasks to be implemented this week:

| Day | Tasks                                                                                                                                                                                                                                      | Start Date | End Date   | Documentation Source |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | ---------- | -------------------- |
| Mon | - Review overall system architecture <br> - Inspect deployed AWS components: <br>&emsp; + Amazon S3 <br>&emsp; + AWS Lambda <br>&emsp; + Amazon DynamoDB <br>&emsp; + Amazon CloudWatch                                                    | 10/08/2026 | 10/08/2026 | -                    |
| Tue | - Test end-to-end image processing workflow: <br>&emsp; + Upload image to system <br>&emsp; + S3 receives file <br>&emsp; + Lambda executes processing <br>&emsp; + Save output image and thumbnail <br>&emsp; + Save metadata to DynamoDB | 11/08/2026 | 11/08/2026 | -                    |
| Wed | - Inspect and evaluate image processing results <br> - Verify metadata records: <br>&emsp; + File information <br>&emsp; + Processing status <br>&emsp; + Compression ratio <br>&emsp; + Processing time                                   | 12/08/2026 | 12/08/2026 | -                    |
| Thu | - Finalize system deployment documentation <br> - Consolidate AWS Service configuration steps <br> - Add illustrative diagrams and execution results                                                                                       | 13/08/2026 | 13/08/2026 | -                    |
| Fri | - Prepare presentation slides and system demonstration <br> - Summarize achievements and results throughout project implementation                                                                                                         | 14/08/2026 | 15/08/2026 | -                    |

### Results achieved in Week 8:

- Completed the **Automatic Image Optimization System on AWS** featuring core components:
  - Amazon S3:
    - Input image storage.
    - Optimized output image storage.
    - Thumbnail storage.

  - AWS Lambda:
    - Automated image processing upon file uploads.
    - Resizing, compression, and thumbnail generation.

  - Amazon DynamoDB:
    - Processing metadata storage.
    - Image processing status tracking.

  - Amazon CloudWatch:
    - Lambda logging and activity monitoring.

- Successfully tested the end-to-end workflow:
  - User uploads an image.
  - Image is stored on Amazon S3.
  - Lambda is triggered automatically.
  - Image is optimized and saved to the output destination.
  - Metadata is recorded in DynamoDB.

- Verified and evaluated post-processing metrics:
  - Image size before and after optimization.
  - Size reduction ratio.
  - Processing time.
  - Processing status.

- Finalized deployment architecture and configuration documentation.

- Prepared presentation content, demo scenarios, and project summary for the **Automatic Image Optimization System on AWS**.
