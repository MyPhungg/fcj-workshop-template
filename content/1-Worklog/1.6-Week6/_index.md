---
title: "Week 6 Worklog"
date: 2026-07-27
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

### Week 6 Objectives:

- Complete image optimization features in the **Automatic Image Optimization System on AWS**.
- Add advanced image processing functionalities such as thumbnail generation, multi-format support, and post-processing metrics calculation.
- Test the end-to-end image processing workflow integrating Amazon S3, AWS Lambda, and Amazon DynamoDB.

### Tasks to be implemented this week:

| Day | Tasks                                                                                                                                                                                                  | Start Date | End Date   | Documentation Source |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------- | ---------- | -------------------- |
| Mon | - Review and finalize image processing logic in AWS Lambda <br> - Test S3 image reading and post-processing output writing <br> - Adjust image processing configurations                               | 27/07/2026 | 27/07/2026 | -                    |
| Tue | - Add thumbnail generation functionality <br> - Build thumbnail storage workflow on Amazon S3 <br> - Verify thumbnail retrieval capability after processing                                            | 28/07/2026 | 28/07/2026 | -                    |
| Wed | - Expand processing capability for multiple image formats: <br>&emsp; + JPEG <br>&emsp; + PNG <br>&emsp; + WEBP <br> - Test format conversion workflow                                                 | 29/07/2026 | 29/07/2026 | -                    |
| Thu | - Add calculation of post-processing metrics: <br>&emsp; + Original size <br>&emsp; + Processed size <br>&emsp; + Compression ratio <br>&emsp; + Processing time                                       | 30/07/2026 | 30/07/2026 | -                    |
| Fri | - Test the entire system: <br>&emsp; + Upload multiple images to S3 <br>&emsp; + Automated Lambda processing <br>&emsp; + Verify output images and thumbnails <br>&emsp; + Verify metadata on DynamoDB | 31/07/2026 | 01/08/2026 | -                    |

### Results achieved in Week 6:

- Completed automated image processing functionality on AWS Lambda.

- Added thumbnail generation capability for images post-processing:
  - Created smaller-sized images for preview purposes.
  - Stored thumbnails on Amazon S3.

- Expanded support for multiple image formats:
  - JPEG.
  - PNG.
  - WEBP.

- Finalized the image optimization process:
  - Resized images according to configurations.
  - Reduced file size.
  - Converted image formats when necessary.

- Added calculation of key metrics to evaluate optimization performance:
  - Original image size.
  - Processed image size.
  - Size reduction ratio.
  - Processing time.

- Successfully tested the end-to-end workflow:
  - Image upload to Amazon S3.
  - S3 triggers AWS Lambda.
  - Lambda executes image optimization.
  - Output images and thumbnails are stored.
  - Metadata is updated in DynamoDB.

- Completed the core core functions of the **Automatic Image Optimization System on AWS**, ready for the monitoring, security, and final refinement phase.
