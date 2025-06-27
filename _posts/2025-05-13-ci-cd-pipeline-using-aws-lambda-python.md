---
layout: post
title: "Automating Lambda Deployment with GitHub Actions: A CI/CD Case Study"
date: 2025-05-12 09:00:00 -0400
categories: [Portfolio]
tags: [ci-cd, github-actions, devops, automation, cloud, aws-lambda, python, technical-writing, madcap-flare, entry-level, portfolio-project]
---

## Context

In the world of cloud applications, development speed and reliability are critical. Manual deployments not only slow down progress but also increase the risk of human error. For this portfolio project, I documented a Continuous Integration and Continuous Deployment (CI/CD) pipeline for a Python-based AWS Lambda function. The pipeline uses GitHub Actions to automate the process of testing and deploying serverless backend code for an affordable housing compliance chatbot. This project mirrors a real-world use case where technical teams want to rapidly ship updates to cloud-native apps without compromising quality or security.

## Solution

The solution involved creating a GitHub Actions workflow that automatically triggers on every push to the `main` branch. The pipeline performs the following steps:
- Installs dependencies using `pip` from a `requirements.txt` file
- Runs unit tests using `pytest`
- Packages the Lambda function by zipping the project
- Deploys the code using the AWS CLI by updating the specified Lambda function

| Step | Action | Tool Used | Purpose |
|------|--------|-----------|---------|
| 1 | Install dependencies | pip | Prepare environment |
| 2 | Run tests | pytest | Validate code quality |
| 3 | Package function (AWS Lambda) | zip | Prepare for deployment |
| 4 | Deploy to AWS | AWS CLI | Update Lambda function |

The process is documented in a MadCap Flare knowledge article format and includes a properly structured `.yml` workflow file located in `.github/workflows/deploy.yml`. This setup can be repurposed for other Python-based Lambda functions, providing a modular and reusable pattern for cloud development teams.


## Impact

If implemented in a real development environment, this pipeline would:
- Eliminate repetitive manual deployment steps
- Reduce deployment errors
- Ensure tested code is automatically shipped to production
- Shorten development feedback loops
- Allow even small teams to maintain DevOps best practices

This approach supports rapid iteration and continuous improvement, which are essential for any scalable cloud-native application.

## Key Takeaways

- CI/CD pipelines can be lightweight yet powerful, especially when leveraging GitHub Actions and AWS CLI
- Python-based serverless applications are easy to test and package with common tools like `pytest` and `zip`
- Using tools like MadCap Flare ensures documentation is clear, repeatable, and enterprise-ready
- Even entry-level implementations of DevOps automation can have significant impact when applied correctly

## Reflection

Before this project, while I understood CI/CD concepts theoretically, I had not documented the pipeline creation process step-by-step. To become more proficient in these processes, I created this documentation during the time I was learning DevOps in AWS Cloud Institute. This project provided hands-on experience to YAML syntax, GitHub Actions workflows, and the structure of real-world DevOps documentation. It also challenged me to explain complex processes in plain language, which improved both my technical writing and cloud architecture knowledge.

### Project Links

> Right-click a link and choose “Open in new tab” if you don’t want to leave this page.
{: .prompt-tip }

> The GitHub Actions workflow used in this project was adapted from a lab exercise in the AWS Cloud Institute DevOps track. I customized it to suit the needs of this project, while also consulting with GitHub Actions Documentation. 
{: .prompt-info }

- [CI/CD Pipeline Knowledge Article (Markdown format)](/assets/ci-cd-pipeline-using-aws-lambda.md)

- [CI/CD Pipeline Knowledge Article (MadCap format - Github Repo)](https://github.com/Alexabeth20/ci-cd-pipeline-doc.git)
