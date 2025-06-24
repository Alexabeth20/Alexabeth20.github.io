---
layout: post
title: "HRM Automation Testing: Streamlining Login Functionality with Selenium"
date: 2025-06-10 12:33:00 +0000
categories: [Portfolio]
tags: [qa, selenium, sutomation, python, hrm, testing]
---

## Context

As part of my QA automation learning journey, I created a test script to automate the login functionality of [OrangeHRM](https://opensource-demo.orangehrmlive.com/), a popular open-source Human Resource Management system. This project served as a practical hands-on exercise to apply what I’ve learned about Selenium WebDriver, Python, and test automation workflows in a real-world UI testing scenario.

The goal was to verify that valid login credentials grant access to the HRM dashboard and that the test can be reliably executed across different runs. This foundational scenario is essential in any application, especially one managing sensitive employee data.

## Solution

I used Python with Selenium WebDriver to write a test script that:

1. Launches a Chrome browser instance.
2. Navigates to the OrangeHRM login page.
3. Enters a valid username and password.
4. Clicks the login button.
5. Verifies successful login by checking for the presence of a dashboard element.
6. Closes the browser.

This script is located in the `test_login.py` file in the [OrangeHRM-Automation-Testing GitHub repository](https://github.com/Alexabeth20/OrangeHRM-Automation-Testing). I structured the test to include assertions and incorporated error handling to manage failed login attempts gracefully.

## Impact

This small but powerful automation script demonstrates how automation testing:

- Saves time on repetitive validation tasks.
- Ensures key functionality—like login—is always working, especially after updates.
- Prevents human error and boosts test coverage early in the software lifecycle.
- Provides a reusable foundation for expanding into more complex HRM workflows (e.g., adding employees, tracking leave).

For businesses, this kind of automation ensures uptime and reliability for critical internal systems like HR platforms—directly impacting productivity and trust in internal tools.

## Key Takeaways

- Selenium is a powerful tool for automating browser-based tests and learning to write stable tests is crucial.
- Even simple tests like login automation offer immense value for both QA learning and enterprise reliability.
- Writing automation scripts early in the development process builds confidence in software releases.
- Automation can—and should—be integrated incrementally to validate mission-critical workflows.

## Reflection

This project reminded me that small wins in automation testing add up to major impact. By successfully validating a core feature, I built both technical skill and QA confidence. I look forward to expanding my skillset with similar projects.

### Project Links

> Right-click a link and choose “Open in new tab” if you don’t want to leave this page.  
{: .prompt-tip }

[HRM Automation Testing Repo](https://github.com/Alexabeth20/OrangeHRM-Automation-Testing)
