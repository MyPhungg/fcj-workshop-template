---
title: "Deploy Backend Infrastructure with AWS CDK"
date: 2026-08-07
weight: 3
chapter: false
pre: " <b> 5.7.3 </b> "
---

---

After completing the environment preparation, the next step is to deploy the Backend infrastructure using **AWS CDK**.

The entire Backend infrastructure is defined as **Infrastructure as Code (IaC)** and organized into 5 CDK Stacks:

- `StorageStack`: Deploys the system's storage resources.
- `ProcessingStack`: Deploys components required for the image processing workflow.
- `BackendStack`: Deploys the application's Backend components.
- `ApiStack`: Deploys API Gateway and configures the connection to the Backend.
- `AmplifyHostingStack`: Configures resources for hosting the Frontend application on AWS Amplify.

These Stacks are deployed through AWS CDK, which enables automatic creation and configuration of AWS resources instead of manually performing these tasks through the AWS Management Console.

---

### Step 1: Clone Source Code and Create Virtual Environment

Clone the project source code from the repository:

```bash id="f1a6mh"
git clone https://github.com/MyPhungg/aws-automatic-image-optimization-system.git
```

After successfully cloning the repository, navigate to the project directory:

```bash id="gr3v1q"
cd aws-automatic-image-optimization-system
```

Create a Python Virtual Environment:

```bash id="y8sx0f"
python -m venv .venv
```

Activate the Virtual Environment.

On **Windows**:

```bash id="1g4q2t"
.venv\Scripts\activate
```

On **Linux/macOS**:

```bash id="5uvq4d"
source .venv/bin/activate
```

After activating the virtual environment, install the required dependencies:

```bash id="7x6c3v"
pip install -r requirements.txt
```

These libraries include the required dependencies for AWS CDK and other related components of the project.

---

### Step 2: Configure Environment Variables

Some configuration values are required during the Backend deployment process. Create a `.env` file at:

```text id="d4t6v7"
backend/image-optimizer/.env
```

Sample content:

```env id="b1t2n4"
GOOGLE_CLIENT_ID=your-google-oauth-client-id
JWT_SECRET=your-secret-key-at-least-32-chars-long
```

Where:

- `GOOGLE_CLIENT_ID`: Google OAuth Client ID used for Google login functionality.
- `JWT_SECRET`: Secret key used for JWT creation and authentication.

Replace the sample values with the actual configuration values of the system.

> **Note:** The `.env` file may contain sensitive information. Do not commit this file to GitHub or share actual secret values.

---

### Step 3: Bootstrap AWS CDK

Before deployment, AWS CDK needs to be **bootstrapped** on the AWS account and region being used.

If the AWS account has not been bootstrapped, execute:

```bash id="q4d9fz"
cdk bootstrap aws://<ACCOUNT_ID>/<REGION>
```

Where:

- `<ACCOUNT_ID>` is the AWS Account ID.
- `<REGION>` is the AWS Region used for deployment.

Example:

```bash id="1s5x3c"
cdk bootstrap aws://123456789012/ap-southeast-1
```

The bootstrap process creates the required resources that allow AWS CDK to deploy applications into the AWS environment.

> **Note:** Normally, each AWS account and region only needs to be bootstrapped once. If the environment has already been bootstrapped, proceed to the deployment step.

---

### Step 4: Deploy Backend Infrastructure

After completing the bootstrap process, deploy all CDK Stacks using the following command:

```bash id="8yq2qf"
cdk deploy --all --require-approval never --outputs-file cdk-outputs.json
```

Where:

- `--all`: Deploys all CDK Stacks in the project.
- `--require-approval never`: Skips manual approval for changes that normally require confirmation during deployment.
- `--outputs-file cdk-outputs.json`: Stores Stack output values in the `cdk-outputs.json` file.

AWS CDK reads the configuration from the source code, identifies the required resources, and creates or updates them in the AWS environment.

After the deployment process is completed, the `cdk-outputs.json` file contains output information generated from the Stacks. These values can be used in the Frontend deployment process and system verification steps.

---

### Step 5: Build Docker Image for Backend

During the deployment process, some Backend Lambda functions are packaged as **Docker Images** through the `DockerImageFunction` configuration.

AWS CDK uses Docker on the local machine to build the corresponding images.

The general workflow is:

```text id="r7m3k2"
AWS CDK
   │
   ▼
Docker Build
   │
   ▼
Docker Image
   │
   ▼
Amazon ECR
   │
   ▼
AWS Lambda
```

Therefore, ensure that **Docker Desktop is running** before executing the `cdk deploy` command.

After the Docker image is successfully built, the image is pushed to **Amazon ECR** and used by Lambda during execution.

> **Note:** The Docker image build process may take additional time depending on the source code size, dependencies, and computer performance.
