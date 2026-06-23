# LoginRequirements.md

# Login Functionality Requirements

## Overview

The purpose of this module is to validate the authentication functionality of the application. The login page allows users to enter credentials and gain access to the application if the credentials are valid.

The automation solution should verify both positive and negative authentication scenarios, validate user feedback messages, and ensure proper navigation behavior after login attempts.

---

# Application Under Test

URL:
https://practicetestautomation.com/practice-test-login/

---

# Business Objective

Ensure that:

* Authorized users can successfully log in.
* Unauthorized users cannot access the application.
* Appropriate validation and error messages are displayed.
* Successful authentication redirects users to the correct page.
* Session management and logout functionality work correctly.

---

# Functional Requirements

## Requirement LR-001: Successful Login

### Description

The application shall allow users to log in using valid credentials.

### Valid Credentials

Username: student

Password: Password123

### Expected Behavior

* User enters valid username.
* User enters valid password.
* User clicks Submit.
* User is redirected to the success page.
* Success message is displayed.
* Logout button is visible.

### Validation Points

* URL changes to success page.
* Success message is displayed.
* Logout button is enabled and visible.

---

## Requirement LR-002: Invalid Username Handling

### Description

The application shall reject login attempts when an invalid username is provided.

### Expected Behavior

* User enters invalid username.
* User enters valid password.
* User clicks Submit.

### Validation Points

* Login is rejected.
* Error message is displayed.
* User remains on login page.

### Expected Message

Your username is invalid!

---

## Requirement LR-003: Invalid Password Handling

### Description

The application shall reject login attempts when an invalid password is provided.

### Expected Behavior

* User enters valid username.
* User enters invalid password.
* User clicks Submit.

### Validation Points

* Login is rejected.
* Error message is displayed.
* User remains on login page.

### Expected Message

Your password is invalid!

---

## Requirement LR-004: Empty Username Validation

### Description

The application should handle attempts where the username field is left empty.

### Expected Behavior

* Username field is blank.
* Password field contains value.
* Submit button is clicked.

### Validation Points

* Login is not successful.
* User remains on login page.
* Appropriate validation behavior is observed.

---

## Requirement LR-005: Empty Password Validation

### Description

The application should handle attempts where the password field is left empty.

### Expected Behavior

* Username entered.
* Password left blank.
* Submit button clicked.

### Validation Points

* Login is rejected.
* User remains on login page.

---

## Requirement LR-006: Empty Credentials Validation

### Description

The application should handle attempts where both fields are empty.

### Expected Behavior

* Username empty.
* Password empty.
* Submit clicked.

### Validation Points

* Authentication fails.
* User remains on login page.

---

## Requirement LR-007: Password Masking

### Description

The password field shall mask entered characters.

### Expected Behavior

* User enters password.

### Validation Points

* Password field type is password.
* Characters are not visible as plain text.

---

## Requirement LR-008: Logout Functionality

### Description

Authenticated users shall be able to terminate their session.

### Expected Behavior

* User logs in successfully.
* User clicks Logout.

### Validation Points

* Session is terminated.
* User redirected appropriately.
* Protected page access is removed.

---

## Requirement LR-009: Page Accessibility

### Description

The login page shall be accessible and load successfully.

### Validation Points

* Page loads without errors.
* Login form elements are visible.
* Submit button is present.

---

# Non-Functional Requirements

* Support execution on Chromium.
* Support execution on Firefox.
* Support execution on WebKit.
* Support parallel execution.
* Capture screenshots on failures.
* Generate execution reports.