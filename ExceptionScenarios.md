# ExceptionScenarios.md

# Dynamic UI and Exception Handling Requirements

## Overview

The purpose of this module is to validate application behavior when interacting with dynamic web elements.

This page intentionally introduces UI behaviors that commonly cause automation failures such as delayed loading, disabled controls, stale references, and dynamic DOM updates.

The automation framework should demonstrate robust synchronization and exception handling techniques.

---

# Application Under Test

URL:
https://practicetestautomation.com/practice-test-exceptions/

---

# Business Objective

Ensure that automation scripts can reliably interact with dynamic web elements and correctly handle asynchronous page behavior.

The framework should validate:

* Dynamic element appearance
* Delayed rendering
* Element state changes
* Editable controls
* Save operations
* DOM refresh scenarios

---

# Functional Requirements

## Requirement ER-001: Dynamic Row Creation

### Description

The application shall create a new row when the Add button is clicked.

### Expected Behavior

* User clicks Add button.
* New row appears dynamically.

### Validation Points

* Row 2 becomes visible.
* Input field is displayed.
* Save button is displayed.

---

## Requirement ER-002: Delayed Element Loading

### Description

The application loads Row 2 after a delay.

### Expected Behavior

* User clicks Add.
* Application performs asynchronous update.

### Validation Points

* Automation waits correctly.
* Row 2 eventually becomes visible.
* No synchronization failures occur.

---

## Requirement ER-003: Save Newly Added Row

### Description

Users shall be able to save data in a dynamically created row.

### Expected Behavior

* User adds Row 2.
* User enters text.
* User clicks Save.

### Validation Points

* Save operation succeeds.
* Success message is displayed.

---

## Requirement ER-004: Disabled Field Protection

### Description

The application prevents editing when a field is disabled.

### Expected Behavior

* Page loads.
* User attempts to edit disabled field.

### Validation Points

* Field remains non-editable.
* No modification occurs.

---

## Requirement ER-005: Enable Editing Mode

### Description

The application allows editing after the Edit button is clicked.

### Expected Behavior

* User clicks Edit.
* Input field becomes editable.

### Validation Points

* Field accepts text entry.
* Disabled state is removed.

---

## Requirement ER-006: Save Updated Data

### Description

Users shall be able to modify and save existing data.

### Expected Behavior

* User clicks Edit.
* User changes field value.
* User clicks Save.

### Validation Points

* Updated value is saved.
* Confirmation message is displayed.

---

## Requirement ER-007: DOM Refresh Handling

### Description

The application dynamically updates the DOM after user actions.

### Expected Behavior

* User performs Add or Save operation.
* DOM elements refresh.

### Validation Points

* Automation re-identifies updated elements.
* Actions continue successfully after refresh.

---

## Requirement ER-008: Element State Verification

### Description

Automation should verify state transitions of controls.

### Expected Behavior

* Elements transition from disabled to enabled.
* Elements become visible after loading.

### Validation Points

* Correct state changes are detected.
* Interaction occurs only when elements are ready.

---

## Requirement ER-009: Success Message Verification

### Description

The application shall provide feedback after successful operations.

### Expected Behavior

* User completes Save action.

### Validation Points

* Success notification appears.
* Message content is verified.

---

## Requirement ER-010: Synchronization Reliability

### Description

Automation should reliably handle delayed UI updates.

### Expected Behavior

* Multiple executions are performed.

### Validation Points

* No flaky failures occur.
* Explicit waits are used where required.
* Tests pass consistently across browsers.

---

# Automation Focus Areas

The framework should demonstrate handling of:

* Dynamic elements
* Delayed loading elements
* Disabled controls
* Editable controls
* DOM refreshes
* Synchronization challenges
* Explicit wait strategies
* Stable locator usage

---

# Non-Functional Requirements

* Cross-browser support.
* Parallel execution support.
* Screenshot capture on failures.
* Detailed execution logging.
* Trace generation for debugging.
* Test execution reporting.