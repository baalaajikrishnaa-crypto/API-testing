# Recorded Results

This document summarizes my API testing practice and validation results using Postman Collection Runner and Newman CLI with the public Simple Tool Rental API.

I have organized the results by portfolio version, keeping earlier practice runs for reference.

## Validation Summary

| Version | Date | Tool | Requests | Assertions Passed | Failures |
|---|---|---|---:|---:|---:|
| V2.0 | 6 Nov 2026 | Postman Runner | 12 | 25 | 0 |
| V2.0 | 6 Nov 2026 | Newman + HTML Extra | 12 | 25 | 0 |
| V1.0 | 1 Nov 2026 | Postman Runner | 9 | 13 | 0 |
| V1.0 | 1 Nov 2026 | Newman + HTML Extra | 9 | 13 | 0 |

All four runs completed successfully with one iteration and no execution errors.

## V2.0 — Final Validation

**Date:** 6 November 2026

For V2.0, I expanded the original collection with additional assertions, automated update verification, and negative test scenarios.

The collection contains 13 requests. I register the API client manually before running the collection, so the automated workflow executes 12 requests.

**Test coverage:**
- API status, tool retrieval, category filtering, and stock information.
- Authenticated order creation, retrieval, updating, and deletion.
- Verification that an updated order comment was saved correctly.
- Negative tests for HTTP 404 and 401 responses.
- Validation of status codes, response data, and expected error messages.

**Execution results:**
- Postman Runner: 12 requests, 25 passing assertions, 0 failures.
- Newman CLI 6.2.3: 12 requests, 25 passing assertions, 0 failures.
- Newman duration: 4.4 seconds.
- Average Newman response time: 353 ms.
- Local HTML report: `local-reports/newman-report-v2.0.html`.

I generated and reviewed the final Newman HTML report in Google Chrome on 6 November 2026.

## V1.0 — Final Validation

**Date:** 1 November 2026

V1.0 was my first complete API testing workflow, covering public endpoints and the authenticated order lifecycle.

The original collection contains 10 requests, with 9 executed automatically after manual API client registration.

**Test coverage:**
- API availability and public tool endpoints.
- Authenticated order creation, listing, retrieval, updating, and deletion.
- Confirmation that a deleted order returns HTTP 404.
- Expected status codes and basic response assertions.
- Manual verification of updated customer information and comments.

**Execution results:**
- Postman Runner: 9 requests, 13 passing assertions, 0 failures.
- Newman CLI 6.2.3: 9 requests, 13 passing assertions, 0 failures.
- Runner duration: 7.089 seconds; average response time: 397 ms.
- Newman duration: 3.6 seconds; average response time: 318 ms.
- HTML Extra Reporter version: 1.23.1.
- Local HTML report: `local-reports/newman-report-v1.0.html`.

The lessons from V1.0 helped me improve the test coverage and add automated update verification in V2.0.

## Earlier Practice Results

**17 October 2026 — Newman**

An earlier course-practice run completed successfully with 9 requests, 13 passing assertions, and zero failures. The original historical HTML report is not included in the repository.

**1 November 2026 — Public GET validation**

Before completing the authenticated workflow, I independently tested three public GET requests, with 7 passing assertions and zero failures.

These tests covered API availability, category filtering, tool selection, and stock information without requiring authentication or creating orders.

## Evidence and Notes

- All results come from actual executions against the public training API, not mocked responses.
- I preserved the V1.0 and V2.0 collection exports separately in `collections/`.
- The exported `apiToken` variable is empty. A valid token must be configured locally before authenticated runs.
- API client registration is a manual setup step and is excluded from automated execution.
- Both Newman HTML reports are stored in `local-reports/`, which is excluded from Git because reports may contain authentication details.
- HTTP 404 and 401 responses are expected outcomes for the corresponding negative tests, not execution failures.
- These results reflect successful executions on the recorded dates. Future results may vary if the public API or its test data changes.