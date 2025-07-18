# Reqres.in – Manual API Testing Project

**A complete manual QA project focusing on core REST API endpoints of Reqres.in**

---

## Project Overview

This repository demonstrates a full manual testing lifecycle of the [Reqres.in](https://reqres.in) demo API, performed over an intensive five-day sprint. It includes:

- **Functional** testing of core API methods (`GET`, `POST`, `PUT`, `PATCH`, `DELETE`)
- **Boundary** and **negative** test coverage
- **Exploratory** testing with malformed payloads, invalid headers, and edge cases
- **Validation** of status codes, error messages, and response structures

**Target Endpoints:** `/users`, `/login`, `/register`, `/unknown`

**Project Timeline:** 26-06-2025 to 30-06-2025 (Completed in 5 days instead of planned 7)

**Note:** As of June 2025, Reqres.in requires all requests to include the following API key header: `x-api-key: reqres-free-v1`

---

## Repository Structure

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
│   ├── Module_Results_PUT_Endpoints.md
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

## Tools & Environment

- **Operating System:** Ubuntu 22.04 LTS
- **API Client:** Postman v10.18.1 and v11.49.3
- **Test Management:** Markdown logs
- **Bug Tracking:** GitHub Issues with markdown templates
- **Editors:** VS Code, LibreOffice
- **Screenshots:** Flameshot, LibreOfficeDraw
- **Version Control:** Git + GitHub

---

## Test Planning & Execution Flow

1. **Day 1:** Create Test Plan, set up folders, define login/register test cases  
2. **Day 2:** Execute login/register tests; exploratory testing; document results  
3. **Day 3:** PUT, PATCH, DELETE test design & execution; capture failures  
4. **Day 4:** GET /unknown cases + retesting logged bugs; finalize execution logs  
5. **Day 5:** Complete defect triage; write Final Report & polish all documentation

All activities are recorded in `Reports/` with exact timestamps and observations.

---

## Test Coverage & Metrics

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

- **Total TC Executed:** 40  
- **Total Bugs Reported:** 12  
- **Average Duration per TC:** ~9–12 minutes  

---

## Notable Defects

**High Severity:**
- No error message when logging in with missing password (`API_24`)

**Medium Severity:**
- PUT/PATCH accept empty bodies without validation (`API_30`, `API_31`)

**Low Severity:**
- Deleting the same user twice returns `204 No Content` instead of `404 Not Found` (`API_36`)

All defects are documented in GitHub Issues with reproduction steps and screenshots, defect screenshos are also documented in `ExecutionResults/Screenshots`.

---

## Exploratory Testing Highlights

1. **Malformed JSON** produces correct `400 Bad Request` responses.  
2. **No Content-Type header** sometimes accepted, showing weak header enforcement.  
3. **No rate-limiting** observed during rapid fire requests to same endpoint.

---

## Recommendations

1. Enforce **mandatory fields** in POST and PATCH bodies.  
2. Improve **status code consistency** (e.g., return 404 when resource is deleted).  
3. Ensure all 4xx errors return **clear messages** in JSON format.  
4. Add **rate-limiting or header validation** to improve robustness.

---

## Conclusion

This project showcases a practical, portfolio-ready example of manual API testing using industry-standard tools and techniques. In just 5 days, all key CRUD and auth flows were tested, 12 bugs reported, and over 40 test cases designed and executed (including exploratory testing).

It demonstrates readiness for a junior QA role, including test design, execution, defect analysis, and thorough documentation.

**The organized structure, execution discipline, and reporting detail reflect strong QA fundamentals and attention to quality. The project can confidently be presented as part of a professional portfolio.**

**Note:** This is a personal portfolio project. A few of the reported bugs were intentionally fabricated to demonstrate defect documentation and reporting skills.

---

*End of README*