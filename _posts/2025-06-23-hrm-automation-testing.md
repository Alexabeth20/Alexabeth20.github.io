---
layout: post
title: "HRM Login Automation Testing with Selenium"
date: 2025-06-10 12:33:00 +0000
categories: [Portfolio]
tags: [qa, selenium, automation, python, hrm, testing]
---

## Context

I created a test script to automate the login functionality of [OrangeHRM](https://opensource-demo.orangehrmlive.com/), a popular open-source Human Resource Management system. This project served as a practical hands-on exercise to apply what I’ve learned about Selenium WebDriver, Python, and test automation workflows in a real-world UI testing scenario.

The goal was to verify that valid login credentials grant access to the HRM dashboard and that the test can be reliably executed across different runs. This foundational scenario is essential in any application, especially one managing sensitive employee data.

## Solution

I used Python with Selenium WebDriver to write a test script that:

1. Launches a Chrome browser instance.
2. Navigates to the OrangeHRM login page.
3. Enters a valid username and password.
4. Clicks the login button.
5. Verifies successful login by checking for the presence of a dashboard element.
6. Closes the browser.

This script is located in the `test_login.py` file in the [OrangeHRM-Automation-Testing GitHub repository](https://github.com/Alexabeth20/OrangeHRM-Automation-Testing).

## Impact

This small automation script demonstrates how automation testing:

- Saves time on repetitive validation tasks.
- Ensures key functionality—like login—is always working, especially after updates.
- Prevents human error and boosts test coverage early in the software lifecycle.
- Provides a reusable foundation to test more complex HRM workflows (e.g., adding employees, tracking leave).

For businesses, this kind of automation increases brand reliability and perception of quality. Buggy apps change customers' perception of the software and directly impact productivity and trust.

## Key Takeaways

- Selenium is a powerful tool for automating browser-based tests.
- Even simple tests, like login automation, offer immense value for both QA learning and enterprise reliability.
- Writing automation scripts early in the development process builds confidence in software releases.
- Integrate automation incrementally to validate mission-critical workflows.

## Reflection


I used AI as a learning tool during this project—asking for guidance on Selenium structure, debugging support, and syntax clarity while ensuring I understood and manually implemented each step.

By validating a core (albeit rudimentary) functionality like login, I built both technical skill and experiential knowledge. This project helped me understand that testing is not just a technical task, it protects organizations from liability and ensures user safety. I look forward to one day expanding my skillset with more complex scenarios involving AI and ML.

### Project Links

> Right-click a link and choose “Open in new tab” if you don’t want to leave this page.  
{: .prompt-tip }

> **Learning Notes:**
This project was developed with AI assistance as a learning tool to understand Selenium and Python automation concepts. I used AI to explain code functionality and guide me through best practices, ensuring I understood each component before implementation. 
{: .prompt-info }

[HRM Automation Testing Repo](https://github.com/Alexabeth20/OrangeHRM-Automation-Testing)
