# Product Design Document (PDD)

# UI Test Automation Framework

## Practice Test Automation Portal

### Version

1.0

### Prepared For

Automation Engineering Team

### Prepared By

QA Automation Architect

### Project Type

Web UI Test Automation Framework

---

# 1. Project Overview

## Objective

Develop a scalable UI automation framework to automate and validate functionality for the following applications:

1. Login Test Portal

   * https://practicetestautomation.com/practice-test-login/

2. Exceptions Test Portal

   * https://practicetestautomation.com/practice-test-exceptions/

The framework should support:

* Functional testing
* Regression testing
* Cross-browser execution
* CI/CD execution
* Reporting and logging
* Parallel execution
* Extensible architecture for future modules

---

# 2. Business Goal

Provide a reusable automation framework that:

* Demonstrates automation engineering capabilities
* Implements automation best practices
* Handles dynamic UI synchronization
* Demonstrates exception handling strategies
* Produces maintainable and scalable test code

---

# 3. Technology Stack

## Recommended

### Automation Tool

Playwright

### Language

TypeScript

### Test Runner

Playwright Test Runner

### Design Pattern

Page Object Model (POM)

### Reporting

Allure Report

### CI/CD

GitHub Actions

### Package Manager

npm

### Code Quality

ESLint
Prettier

---

# 4. Application Analysis

---

## Module A: Login Portal

### URL

https://practicetestautomation.com/practice-test-login/

### Available Functionality

Fields:

* Username
* Password

Actions:

* Submit Button

Success Page:

* Congratulations message
* Logout button

Negative Responses:

* Invalid username message
* Invalid password message

Valid Credentials:

Username: student

Password: Password123

Source verification from application test instructions.

---

## Module B: Exceptions Portal

### URL

https://practicetestautomation.com/practice-test-exceptions/

### Available Functionality

Page contains:

* Row 1 Input
* Edit Button
* Save Button
* Add Button

Dynamic Behaviors:

* New row added asynchronously
* Delayed element loading
* Disabled controls
* DOM refresh causing stale references

Purpose:

Simulate Selenium/UI automation exceptions including:

* NoSuchElementException
* ElementNotInteractableException
* InvalidElementStateException
* StaleElementReferenceException
* TimeoutException

---

# 5. Functional Requirements

---

# 5.1 Login Module Automation

## Login_TC_001

### Title

Verify successful login

### Steps

1. Navigate to Login page
2. Enter valid username
3. Enter valid password
4. Click Submit

### Expected Results

* User redirected successfully
* URL contains logged-in-successfully
* Success message visible
* Logout button displayed

---

## Login_TC_002

### Title

Verify invalid username

### Steps

1. Enter incorrect username
2. Enter valid password
3. Click Submit

### Expected Results

* Error displayed
* Message:
  "Your username is invalid!"

---

## Login_TC_003

### Title

Verify invalid password

### Steps

1. Enter valid username
2. Enter invalid password
3. Click Submit

### Expected Results

* Error displayed
* Message:
  "Your password is invalid!"

---

## Additional Coverage

### Login_TC_004

Blank username

Expected:
Validation/Error displayed

---

### Login_TC_005

Blank password

Expected:
Validation/Error displayed

---

### Login_TC_006

Blank username and password

Expected:
Submission rejected

---

### Login_TC_007

Verify password field masking

Expected:
Characters hidden

---

### Login_TC_008

Verify page title

Expected:
Correct title displayed

---

### Login_TC_009

Verify URL accessibility

Expected:
Page loads successfully

---

### Login_TC_010

Verify logout functionality

Expected:

* User logged out
* Redirected appropriately

---

# 5.2 Exception Module Automation

---

## Exception_TC_001

### Title

Verify Row 2 appears after Add

### Purpose

Validate dynamic element loading

### Steps

1. Open page
2. Click Add
3. Wait for Row 2

### Expected

* Row 2 displayed

---

## Exception_TC_002

### Title

Verify Save after entering Row 2 data

### Steps

1. Add Row 2
2. Wait for load
3. Enter value
4. Click correct Save button

### Expected

* Data saved
* Confirmation message displayed

---

## Exception_TC_003

### Title

Verify editing disabled field

### Steps

1. Open page
2. Attempt to type without clicking Edit

### Expected

* Field not editable

---

## Exception_TC_004

### Title

Verify Edit enables input field

### Steps

1. Click Edit
2. Enter text

### Expected

* Field becomes editable

---

## Exception_TC_005

### Title

Verify Save persists edited value

### Steps

1. Click Edit
2. Modify text
3. Save

### Expected

* Value retained

---

## Exception_TC_006

### Title

Verify instruction element removal

### Steps

1. Capture instruction element
2. Click Add

### Expected

* Element removed
* DOM updated

---

## Exception_TC_007

### Title

Verify explicit wait strategy

### Steps

1. Click Add
2. Wait until Row 2 visible

### Expected

* Test passes consistently

---

## Exception_TC_008

### Title

Verify timeout handling

### Steps

1. Use short timeout
2. Wait for Row 2

### Expected

* Timeout captured
* Framework logs failure

---

# 6. Non-Functional Requirements

## Cross Browser

Support:

* Chromium
* Firefox
* WebKit

---

## Parallel Execution

Support concurrent execution

Target:

* 3 browser execution

---

## Reporting

Allure Reports should include:

* Test summary
* Screenshots
* Failure details
* Execution duration

---

## Logging

Framework must generate:

* Test execution logs
* Browser actions
* Failure logs

---

# 7. Framework Architecture

```text
project-root
|
├── tests
│   ├── login
│   └── exceptions
|
├── pages
│   ├── LoginPage.ts
│   ├── SuccessPage.ts
│   └── ExceptionsPage.ts
|
├── fixtures
|
├── utils
│   ├── waitUtils.ts
│   ├── logger.ts
│   └── screenshot.ts
|
├── test-data
│   └── credentials.json
|
├── reports
|
├── playwright.config.ts
|
└── package.json
```

---

# 8. Page Object Model Design

## LoginPage

Methods:

```typescript
navigate()
enterUsername()
enterPassword()
clickSubmit()
getErrorMessage()
```

---

## SuccessPage

Methods:

```typescript
verifySuccessMessage()
verifyLogoutButton()
logout()
```

---

## ExceptionsPage

Methods:

```typescript
clickAdd()
clickEdit()
clickSave()
enterRow2Text()
waitForRow2()
getSuccessMessage()
```

---

# 9. Test Data Strategy

## Valid Credentials

```json
{
  "username": "student",
  "password": "Password123"
}
```

## Invalid Credentials

```json
{
  "invalidUser": "wrongUser",
  "invalidPassword": "wrongPassword"
}
```

Store externally.

No hardcoded values in tests.

---

# 10. Error Handling Strategy

Framework should automatically:

* Capture screenshots on failure
* Record browser console logs
* Record Playwright traces
* Attach artifacts to Allure

---

# 11. CI/CD Pipeline

## Trigger

* Pull Request
* Push to Main Branch
* Manual Run

Pipeline Steps:

1. Install dependencies
2. Run linting
3. Execute tests
4. Generate Allure report
5. Publish report artifact

---

# 12. Success Criteria

Project is considered complete when:

* 100% planned scenarios automated
* Cross-browser execution successful
* Reporting integrated
* CI pipeline operational
* Framework documentation completed

---

# 13. Future Enhancements

* API automation integration
* Visual testing
* Accessibility testing
* Dockerized execution
* Cloud execution
* Data-driven testing
* BDD implementation with Cucumber

---

# Deliverables

1. Automation Framework
2. Source Code Repository
3. Test Reports
4. CI/CD Pipeline
5. Execution Guide
6. Framework Documentation
7. Automated Regression Suite

END OF DOCUMENT