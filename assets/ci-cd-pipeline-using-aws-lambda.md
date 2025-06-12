# CI/CD Pipeline for AWS Lambda Using GitHub Actions (Python)

**Article #:** CI-001  
**Product:** GitHub Actions  
**Version:** 1.0

---

## Summary

This article outlines how to configure a GitHub Actions CI/CD pipeline to deploy a Python-based AWS Lambda function. It includes setting up dependencies, testing, packaging, and deployment using the AWS CLI.

---

## Full Description

This CI/CD pipeline uses GitHub Actions to automate the process of building, testing, and deploying a Python Lambda function to AWS. The deployment is triggered by a push to the `main` branch. GitHub Actions installs project dependencies, runs unit tests with pytest, zips the Lambda function, and uses the AWS CLI to push code to an existing Lambda function.

**Prerequisites:**
- AWS account with a deployed Lambda function
- IAM user with programmatic access and Lambda update permissions
- GitHub repository with Python Lambda source code
- A `requirements.txt` file for dependencies
- `pytest` installed for test execution

---

## Solution

1. Create the workflow file in your project directory at:  
   `.github/workflows/deploy.yml`

2. Paste the following YAML into the file:

```yaml
name: Deploy Python Lambda

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v3

    - name: Set up Python
      uses: actions/setup-python@v4
      with:
        python-version: '3.11'

    - name: Install dependencies
      run: |
        python -m pip install --upgrade pip
        pip install -r requirements.txt

    - name: Run tests
      run: |
        pytest

    - name: Zip Lambda function
      run: |
        zip -r function.zip . -x "*.git*" -x "*tests*"

    - name: Configure AWS credentials
      uses: aws-actions/configure-aws-credentials@v3
      with:
        aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
        aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
        aws-region: us-east-1

    - name: Deploy to AWS Lambda
      run: |
        aws lambda update-function-code \
          --function-name YourLambdaFunctionName \
          --zip-file fileb://function.zip
