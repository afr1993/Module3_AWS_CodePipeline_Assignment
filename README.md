# Module3_AWS_CodePipeline_Assignment
# 🚀 AWS CodePipeline: Static Website Deployment to S3

This project demonstrates a fully automated CI/CD pipeline using **AWS CodePipeline** to deploy a static website to an **S3 bucket configured for static website hosting**.

---

## 📁 Project Structure

sitio-estatico/
├── index.html
└── README.md

---

## ⚙️ Pipeline Overview

The pipeline consists of the following stages:

1. **Source Stage**:
   - Source: GitHub repository (`main` branch).
   - Trigger: A commit to the branch automatically starts the pipeline.

2. **(Optional) Build Stage**:
   - Skipped for static sites (no build required).

3. **Deploy Stage**:
   - Target: Amazon S3 bucket configured for static website hosting.
   - Files are extracted and uploaded to S3 upon every commit.

---

## 🧪 Prerequisites

- AWS account with sufficient permissions (S3, CodePipeline, IAM).
- A GitHub account with a repository containing `index.html`.
- An S3 bucket created and configured for static website hosting.

---

## 🪜 Setup Instructions

### 1. Create S3 Bucket
- Go to **Amazon S3** → **Create bucket**
- Name must be globally unique.
- Uncheck **Block all public access**
- Enable **Static Website Hosting** in the **Properties** tab:
  - Index document: `index.html`

### 2. Set Bucket Policy
Allow public access to your files:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowPublicReadAccessToObjects",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::mi-sitio-estatico-bucket-adrian/*"
    }
  ]
}

3. Create GitHub Repository

git init
git add .
git commit -m "Initial commit"
git remote add origin 
git push -u origin main
4. Create CodePipeline
Go to AWS CodePipeline → Create pipeline:

Pipeline settings:

Name: SitioEstaticoPipeline

Create new service role (recommended)

Source:

Provider: GitHub

Connect account & select your repo and main branch

Build:

Skip build stage (not needed)

Deploy:

Provider: Amazon S3

Bucket: Select your static site bucket

✅ Check Extract file before deploy

🧪 Test the Pipeline
Modify index.html

Commit and push changes to GitHub:


git add index.html
git commit -m "Update homepage"
git push
CodePipeline triggers automatically and deploys to S3.



