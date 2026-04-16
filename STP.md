# Software Test Plan (STP) - GoRest API Automation

## 1. Introduction
This document defines the test strategy and plan for validating the **Users** resource of the GoRest Public API. The focus is on ensuring data consistency, proper HTTP response handling, and robust validation of business logic.

## 2. Test Objectives
* Verify all CRUD operations (Create, Read, Update, Delete) are functional.
* Validate JSON Schema for all response bodies.
* Ensure proper error handling for invalid data (Negative Testing).
* Monitor API performance (Response Time).

## 3. Scope
* **In Scope:** * Endpoints: `/public/v2/users`
    * Methods: GET, POST, PUT, PATCH, DELETE.
    * Data validation: Email format, required fields, and unique constraints.
* **Out of Scope:** * UI Testing.
    * Load/Stress testing (beyond basic response time checks).
    * Other GoRest resources (Posts, Comments, etc.).

## 4. Test Strategy & Methods
| Methodology | Description |
| :--- | :--- |
| **Positive Testing** | Validating that the API behaves as expected with valid inputs (Happy Path). |
| **Negative Testing** | Sending malformed JSON, invalid emails, and missing required fields to verify 422/400 error codes. |
| **Security Testing** | Validating that requests without a valid Bearer Token return a 401 Unauthorized status. |
| **Data Chaining** | Creating a user and using the returned `id` for subsequent GET/PUT/DELETE requests. |

## 5. Environment & Tools
* **Testing Tool:** Postman Desktop
* **Language:** JavaScript (Postman Sandbox)
* **API Documentation:** [GoRest Docs](https://gorest.co.in/)
* **Version Control:** GitHub

## 6. Risks & Mitigations
* **Risk:** Third-party API (GoRest) downtime or maintenance.
* **Mitigation:** Tests are designed to be environment-independent; failures will be analyzed to distinguish between environment issues and code bugs.
* **Risk:** Data persistence in a public sandbox.
* **Mitigation:** Using dynamic data generation (Dynamic Variables) in Pre-request scripts to ensure every test run uses fresh data.

## 7. Entry & Exit Criteria
* **Entry:** API Documentation is available and Auth Token is generated.
* **Exit:** All automated tests in the collection pass (100% pass rate) and all negative scenarios are documented.
