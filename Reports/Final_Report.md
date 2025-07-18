# Final Report – Reqres.in API Manual Testing Project

**Project:** Manual Testing of RESTful API Endpoints on Reqres.in Demo Site\
**Tester:** Aleksa Aleksić\
**Duration:** 24-06-2025 to 29-06-2025\
**Base URL:** [https://reqres.in](https://reqres.in)

---

## 1. Introduction

This report outlines the results of a focused manual testing effort targeting the REST API endpoints provided by **Reqres.in**, a publicly available API testing playground. The project was executed across five structured workdays and included positive, negative, boundary, and exploratory testing techniques.

Particular attention was paid to input validation, error handling, REST compliance, response consistency, and defect tracking using reproducible steps and screenshots. All testing was executed manually via Postman, with detailed execution logs and formal documentation in Markdown format.

---

## 2. Scope & Objectives

**Scope:**

- Functional validation of endpoints: `GET`, `POST`, `PUT`, `PATCH`, `DELETE`
- Focused testing on endpoints: `/users`, `/login`, `/register`, `/unknown`
- Testing API behavior with valid, missing, and malformed JSON payloads
- Exploratory testing of input validation, rate limiting, and error messaging
- Full defect documentation with screenshot evidence and reproduction steps

**Objectives:**

1. Validate core API functionality and expected HTTP status codes.
2. Evaluate behavior with both valid and invalid requests.
3. Identify inconsistent or missing error messages and log them as defects.
4. Create a test suite and artifacts suitable for a professional QA portfolio.

---

## 3. Test Environment & Tools

**Operating System:**

- Ubuntu 22.04 LTS

**Tools & Utilities:**

- **API Client:** Postman v10.18.1, v11.49.3
- **Test Management:** Markdown logs
- **Bug Tracking:** GitHub Issues
- **Documentation:** VS Code / LibreOffice Writer
- **Screenshots:** Flameshot / LibreOffice Draw
- **Version Control:** Git & GitHub

---

## 4. Folder Structure & Artifacts

```
~/ReqresTesting/
├── TestPlan/
│   └── Reqres_Test_Plan.md
├── TestCases/
│   ├── DELETE_users_id_Test_Cases.md
│   ├── GET_unknown_id_Test_Cases.md
│   ├── GET_users_id_Test_Cases.md
│   ├── GET_users_page_n_Test_Cases.md
│   ├── PATCH_users_id_Test_Cases.md
│   ├── POST_login_Test_Cases.md
│   ├── POST_register_Test_Cases.md
│   ├── PUT_users_id_Test_Cases.md
│   └── Reqres_API_TC.md
├── TestData/
│   ├── invalid_payloads.json
│   └── valid_payloads.json
├── ExecutionResults/
│   ├── Bug_Retest_Results.md
│   ├── Module_Results_DELETE_Endpoints.md
│   ├── Module_Results_GET_Endpoints.md
│   ├── Module_Results_GET_unknown_Endpoints.md
│   ├── Module_Results_PATCH_Endpoints.md
│   ├── Module_Results_POST_Endpoints.md
│   ├── Module_Results_PUT_Endpoints
│   └── Screenshots/
├── Reports/
│   ├── Daily_Report_24-06-2025.md
│   ├── Daily_Report_25-06-2025.md
│   ├── Daily_Report_26-06-2025.md
│   ├── Daily_Report_27-06-2025.md
│   ├── Daily_Report_28-06-2025.md
│   └── Final_Report.md
└── README.md
```

---

## 5. Test Case Coverage

A total of **40 test cases** were manually designed and executed:

- **GET /users?page={n}:** 8 cases
- **GET /users/{id}:** 6 cases
- **POST /register:** 8 cases
- **POST /login:** 6 cases
- **PUT /users/{id}:** 3 cases
- **PATCH /users/{id}:** 3 cases
- **DELETE /users/{id}:** 3 cases
- **GET /unknown/{id}:** 3 cases
- **Negative & Exploratory scenarios:** 10+ additional tests

Each test case included:

- **ID**, **Title**, **Steps**, **Expected Result**, **Actual Result**, **Status**, **Type**, **Priority**

---

## 6. Execution Summary

| Endpoint       | Method | TC | PASS | FAIL | Exploratory (min) | Bugs Logged |
| -------------  | ------ | -- | ---- | ---- | ----------------- | ----------- |
| /login         | POST   | 6  | 5    | 1    | 25                | 1           |
| /register      | POST   | 8  | 6    | 2    | 25                | 2           |
| /users/{id}    | PUT    | 3  | 1    | 2    | 30                | 2           |
| /users/{id}    | PATCH  | 3  | 1    | 1    | 25                | 1           |
| /users/{id}    | DELETE | 3  | 2    | 1    | 20                | 1           |
| /users?page={n}| GET    | 8  | 5    | 3    | 30                | 3           |
| /users/{id}    | GET    | 6  | 4    | 2    | 30                | 2           |
| /unknown/{id}  | GET    | 3  | 3    | 0    | 20                | 0           |

**Total Execution Time:** \~20 hours\
**Total Bugs Logged:** 12

---

## 7. Defect Analysis Highlights

**Defects by Severity:**

- **High:** 4 (no error message on missing password)
- **Medium:** 8 (silent 200 OKs on empty/invalid PUT/PATCH Endpoints)

**Root Causes:**

- Lack of input validation on server side for PUT/PATCH
- Incorrect handling of resource lifecycle (DELETE)
- Missing error body for essential POST failures

---

## 8. Exploratory Testing Highlights

1. **Malformed JSON Payloads:** Sending malformed JSON results in `400 Bad Request` as expected.
2. **Missing Content-Type Header:** Without `Content-Type: application/json`, some endpoints still accept body silently.
3. **Rate Limits:** No observable throttling or rate limit headers after repeated rapid requests.

---

## 9. Lessons Learned & Recommendations

1. **Standardized Error Handling:** All 4xx responses should include descriptive error messages.
2. **Stricter PUT/PATCH Validation:** Server should reject empty or invalid payloads.
3. **Lifecycle Consistency:** Deleting an already-deleted user should return `404`.
4. **Exploratory Testing is Valuable:** Several bugs were only discovered through unplanned inputs.
5. **Structured Execution with Screenshots Adds Clarity:** Markdown logging and screenshots created traceability.

---

## 10. Conclusion

The Reqres.in API manual testing project demonstrates end-to-end testing of a demo REST API through structured and exploratory methods. A total of 40 test cases were executed across multiple endpoints, resulting in 4 valid and documented defects.

Test planning, test case writing, execution logs, defect reporting, and daily/final reports were produced to simulate a real-world QA cycle. The project serves as a strong portfolio piece for junior QA roles, showcasing knowledge of HTTP methods, status codes, REST validation, test case design, and defect reporting standards.

All findings were carefully documented with timestamps, screenshots, and Markdown traceability.

---
