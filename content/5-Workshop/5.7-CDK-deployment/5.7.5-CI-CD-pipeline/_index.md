---
title: "CI/CD Deployment with GitHub Actions"
date: 2026-08-07
weight: 5
chapter: false
pre: " <b> 5.7.5 </b> "
---

---

After completing the manual deployment process, the team uses **GitHub Actions** to automate the **Continuous Integration and Continuous Deployment (CI/CD)** process.

The workflow is defined in the following file:

```text
.github/workflows/deploy.yml
```

Whenever new changes are pushed to the `main` branch, GitHub Actions automatically performs the necessary steps to update the Backend and Frontend in the AWS environment.

### Step 1: Configure GitHub Secrets

To allow GitHub Actions to access and deploy resources on AWS, authentication information must be configured as **GitHub Secrets**.

Access the project's repository on GitHub, then select:

**Settings → Secrets and variables → Actions**

Add the following Secrets:

| Secret                  | Description                                                                                        |
| ----------------------- | -------------------------------------------------------------------------------------------------- |
| `AWS_ACCESS_KEY_ID`     | Access Key of the IAM User used to deploy AWS resources                                            |
| `AWS_SECRET_ACCESS_KEY` | Corresponding Secret Access Key                                                                    |
| `AWS_SESSION_TOKEN`     | Session Token, used when AWS credentials are temporary credentials such as AWS Academy credentials |
| `VITE_GOOGLE_CLIENT_ID` | Google OAuth Client ID used for Google login                                                       |

> **Note:** `AWS_SESSION_TOKEN` is only required when using temporary credentials. When using standard Access Key/Secret Key credentials, this Secret may not be required.

The authentication information is stored as GitHub Secrets to prevent credentials from being directly exposed in the source code.

---

### Step 2: Trigger the CI/CD Pipeline

The workflow is configured to run whenever new code is pushed to the `main` branch.

The general process is as follows:

```text
Developer
    │
    │ git push
    ▼
GitHub Repository
    │
    ▼
GitHub Actions
    │
    ├──► Setup Python
    │
    ├──► Setup Node.js
    │
    ├──► Install AWS CDK
    │
    ├──► Deploy Backend
    │
    ├──► Get CDK Outputs
    │
    ├──► Build Frontend
    │
    └──► Deploy to AWS Amplify
```

This allows developers to avoid manually executing the entire deployment process after every source code update.

---

### Step 3: Deploy the Backend

After the workflow is triggered, GitHub Actions prepares the required environment for the project, including Python, Node.js, and AWS CDK.

The workflow then deploys the CDK Stacks using the following command:

```bash
cdk deploy --all
```

Changes in the CDK source code are checked and deployed to the AWS environment.

If the Backend deployment is successful, the CDK output values are used in the subsequent steps of the pipeline.

---

### Step 4: Retrieve Information from CDK Outputs

After the Backend deployment is completed, the workflow retrieves the required values from the CDK outputs, such as:

- `ApiGatewayUrl`: The API Gateway URL used by the Frontend.
- `AmplifyAppId`: The ID of the AWS Amplify application.

These values allow the pipeline to configure and deploy the Frontend using the Backend resources that have just been updated.

---

### Step 5: Build the Frontend

After retrieving the API Gateway URL, the workflow builds the React/Vite application.

The API environment variable is configured so that the Frontend uses the latest API Gateway URL:

```text
VITE_API_GATEWAY_URL
```

The application is then built into static files for deployment:

```bash
npm install
npm run build
```

The build output is generated in the `dist` directory.

---

### Step 6: Deploy the Frontend to AWS Amplify

After the Frontend is successfully built, the workflow packages the files in the `dist` directory and deploys them to **AWS Amplify**.

This process updates the latest Frontend version in the Live environment without requiring manual deployment through the **AWS Management Console**.

Once the deployment is completed, users can access the latest version of the application through the URL provided by AWS Amplify.

---

### Verify the CI/CD Pipeline

After pushing code to the `main` branch, the workflow execution can be monitored by following these steps:

1. Access the project's repository on GitHub.
2. Select the **Actions** tab.
3. Select the deployment workflow.
4. Monitor the status of each step.
5. Verify that the workflow completes successfully.

If all steps are completed successfully, the Backend and Frontend have been successfully updated in the AWS environment.

#### Result

After the CI/CD Pipeline is configured, the system deployment process is automated as follows:

```text
Push code to main
        │
        ▼
GitHub Actions
        │
        ├──► Deploy AWS CDK
        │
        ├──► Retrieve API Gateway URL
        │
        ├──► Build React Frontend
        │
        └──► Deploy to AWS Amplify
```

Implementing CI/CD helps reduce manual deployment tasks, minimize errors during system updates, and shorten the time required to deliver new versions to the AWS environment.
