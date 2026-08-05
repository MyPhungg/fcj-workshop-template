---
title: "Week 5 Worklog"
date: 2026-07-20
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

### Week 5 Objectives:

- Build metadata storage functionality for the **Automatic Image Optimization System on AWS**.
- Connect AWS Lambda with Amazon DynamoDB to store image processing details.
- Track processing status and image file-related information.

### Tasks to be implemented this week:

| Day | Tasks                                                                                                                                                                                                                         | Start Date | End Date   | Documentation Source                      |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------- | ---------- | ----------------------------------------- |
| Mon | - Research Amazon DynamoDB for metadata storage <br> - Determine information to be stored: <br>&emsp; + Image file information <br>&emsp; + Processing status <br>&emsp; + Processing time <br>&emsp; + File size information | 20/07/2026 | 20/07/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Tue | - Create DynamoDB Table for storing Image Metadata <br> - Design data structure: <br>&emsp; + Partition Key <br>&emsp; + Sort Key <br>&emsp; + Other metadata attributes                                                      | 21/07/2026 | 21/07/2026 | <https://cloudjourney.awsstudygroup.com/> |
| Wed | - Update AWS Lambda Function to connect to DynamoDB <br> - Configure IAM permissions to allow Lambda access to DynamoDB <br> - Perform metadata data writing after image processing completion                                | 22/07/2026 | 22/07/2026 | -                                         |
| Thu | - Build processing status update mechanism: <br>&emsp; + PROCESSING <br>&emsp; + SUCCESS <br>&emsp; + FAILED <br> - Log error details when processing fails                                                                   | 23/07/2026 | 23/07/2026 | -                                         |
| Fri | - Verify metadata records on DynamoDB <br> - Test the end-to-end processing workflow: <br>&emsp; + Upload image <br>&emsp; + Lambda processes image <br>&emsp; + Store output image <br>&emsp; + Save metadata                | 24/07/2026 | 25/07/2026 | -                                         |

### Results achieved in Week 5:

- Successfully created a DynamoDB Table for image metadata storage.

- Designed a comprehensive metadata data structure, including:
  - Identification details:
    - Batch ID.
    - Processing ID.

  - File details:
    - Original name.
    - Input bucket.
    - Output bucket.
    - Input key.
    - Output key.

  - Processing details:
    - Processing status.
    - Processing time.
    - Error message.

  - File size details:
    - Original size.
    - Processed size.
    - Compression ratio.

- Successfully connected AWS Lambda to DynamoDB to save post-processing data.

- Built a processing status update mechanism:
  - **PROCESSING:** Lambda is currently processing the image.
  - **SUCCESS:** Processing completed successfully.
  - **FAILED:** An error occurred during processing.

- Verified data recorded on DynamoDB after Lambda execution completed.

- Completed metadata management functionality, enabling the system to monitor information and track status for each image during processing.
