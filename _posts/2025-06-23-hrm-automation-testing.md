---
layout: post
title: "HRM Login Automation Testing with Selenium"
date: 2025-06-10 12:33:00 +0000
categories: [Portfolio]
tags: [qa, selenium, automation, python, hrm, testing]
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

This script is located in the `test_login.py` file in the [OrangeHRM-Automation-Testing GitHub repository](https://github.com/Alexabeth20/OrangeHRM-Automation-Testing).

## Impact

This small but powerful automation script demonstrates how automation testing:

- Saves time on repetitive validation tasks.
- Ensures key functionality—like login—is always working, especially after updates.
- Prevents human error and boosts test coverage early in the software lifecycle.
- Provides a reusable foundation for expanding into more complex HRM workflows (e.g., adding employees, tracking leave).

For businesses, this kind of automation ensures uptime and reliability for critical internal systems like HR platforms—directly impacting productivity and trust in internal tools.

## Key Takeaways

- Selenium is a powerful tool for automating browser-based tests.
- Even simple tests, like login automation, offer immense value for both QA learning and enterprise reliability.
- Writing automation scripts early in the development process builds confidence in software releases.
- Automation can—and should—be integrated incrementally to validate mission-critical workflows.

## Reflection

This was my very first automation test, and while it may be rudimentary, it represents a meaningful milestone: my commitment to learn, grow, and pursue and test the waters in QA automation. I created this test independently using Python and Selenium, combining online research with hands-on experimentation.

By validating a core functionality like login, I built both technical skill and experiantial knowledge. This project helped me understand that testing is not just a technical task, it protects organizations from liability and ensure user's safety. I look forward to one day expanding my skillset with more complex scenarios involving AI and ML.

### Project Links

> Right-click a link and choose “Open in new tab” if you don’t want to leave this page.  
{: .prompt-tip }

> This was my very first automation test project—created while learning Python and testing fundamentals through the AWS Cloud Institute. It may be simple, but it marks the start of my QA journey and shows my ability to learn and take initiative.  
{: .prompt-info }

[HRM Automation Testing Repo](https://github.com/Alexabeth20/OrangeHRM-Automation-Testing)
