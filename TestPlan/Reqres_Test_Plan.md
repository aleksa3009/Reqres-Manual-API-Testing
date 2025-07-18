
# Test Plan: Reqres.in - Manual Testing of REST API Endpoints

**Author:** Aleksa Aleksić  
**Date:** 25.6.2025
**Version:** 2.0
**Project:** Reqres.in REST API Manual Testing  
**Base URL:** [https://reqres.in/api](https://reqres.in/api)

---

## 1. Introduction  
This document serves as the formal test plan for manual testing of the public REST API endpoints provided by Reqres.in. The goal of the project is to verify the correctness of CRUD operations, validate HTTP status codes and JSON schema compliance, as well as test error handling and performance response times. This plan outlines the testing strategy, scope, resources, and schedule. It aims to demonstrate a structured and professional QA approach suitable for inclusion in a junior QA portfolio.

---

## 2. Scope

**In Scope:**  
- Functional manual testing of the following API endpoints:  
  - **GET /users?page={n}**
  - **GET /users/{id}**  
  - **POST /register**
  - **POST /login**  
  - **PUT /users/{id}** 
  - **PATCH /users/{id}**  
  - **DELETE /users/{id}**  
  - **GET /unknown** 
  - **GET /unknown/{id}**  
- **Validation of HTTP status codes** (200, 201, 400, 404, etc.)  
- **Verification of JSON schema** and response data correctness  
- **Negative and boundary testing** including invalid inputs, missing fields, and incorrect data types  
- Recording **response times** and flagging slow responses (> 3 seconds)  
- Defect logging and tracking in **GitHub Issues**
- Manual execution of test cases using **Postman** and documentation of results in **Markdown** format  

**Out of Scope:**  
- **Automated testing** (e.g., scripting with Postman, REST Assured, or CI integration)  
- **Security testing** (token validation, authentication exploits)  
- Extensive **performance or load testing**
- **Modifications to backend or database** (testing is limited to publicly available responses only)  

---

## 3. Objectives  
**1.** Confirm all API endpoints behave as expected with valid and invalid inputs  
**2.** Ensure all JSON responses comply with expected schema and contain required fields  
**3.** Validate proper error messages and status codes on invalid requests  
**4.** Measure and document API response times, highlighting any delays  
**5.** Log defects with clear reproduction steps, payloads, and expected vs. actual results  
**6.** Deliver professional test artifacts including test cases, execution logs, defect reports, and summary documentation  

---

## 4. Roles and Responsibilities

| Role        | Name           | Responsibility                                           |
|-------------|----------------|---------------------------------------------------------|
| Tester      | Aleksa Aleksić | Create test plan, design and execute test cases, log and track defects |
| Reviewer    | Aleksa Aleksić| Review test artifacts and provide feedback              |
| Stakeholder | Aleksa Aleksić | Analyze and resolve reported issues based on test findings |

---

## 5. Test Items

| Endpoint               | Description                                               |
|------------------------|-----------------------------------------------------------|
| GET /users?page={n}    | Validate user list pagination and response correctness    |
| GET /users/{id}        | Retrieve individual users by ID, test valid and invalid IDs |
| POST /register         | User registration with valid and invalid payloads        |
| POST /login            | User login with correct and incorrect credentials         |
| PUT /users/{id}        | Full update of user data                                  |
| PATCH /users/{id}      | Partial update of user data                               |
| DELETE /users/{id}     | Delete user resource and verify deletion                  |
| GET /unknown           | Validate resource metadata list                            |
| GET /unknown/{id}      | Retrieve single resource metadata with valid and invalid IDs |

---

## 6. Test Approach and Strategy

1. **Test Types:** Functional, boundary, negative and exploratory testing (to discover edge cases and unexpected issues) 
2. **Test Design:**  
   - Risk-based prioritization focusing on high-impact endpoints and common failure points  
   - Detailed, step-by-step test cases documented in Markdown  
3. **Execution Order:**  
   1. GET endpoints (list and single user)  
   2. POST endpoints (register and login)  
   3. PUT, PATCH, DELETE endpoints  
   4. GET unknown endpoints  
4. **Environment:** Testing manually using the latest stable Postman client (including JSON Schema validation), on Linux OS  
5. **Defect Management:** Logging all bugs in GitHub Issues with detailed reproduction steps, request payloads, response screenshots, and status tracking 
6. **Performance:** Measure response times and flag any responses exceeding 3 seconds  

---

## 7. Environment and Tools

- **Operating Systems:** Ubuntu 22.04 LTS  
- **API Client:** Postman v11.54.0 (latest stable version) 
- **Validation:** JSON Schema validation via Postman tests  
- **Bug Tracking:** GitHub Issues  
- **Editor:** Visual Studio Code  
- **Version Control:** Git & GitHub  
- **Reporting:** Markdown files stored in `Reports/` folder  

---

## 8. Entry Criteria

- Project directory structure set up (`~/ReqresTesting/`)  
- Postman and other tools installed and configured  
- Access to GitHub repository for bug tracking  
- Valid and invalid JSON payloads prepared in `TestData/` folder  
- Test case template and defect report templates ready  

---

## 9. Exit Criteria

**Module-Level Exit Criteria:**  
- All test cases executed with PASS/FAIL results recorded  
- Defects logged with full reproduction details and attachments  
- Exploratory testing completed and findings documented  
- Daily summary reports created  

**Project-Level Exit Criteria:**  
- All endpoint modules meet exit criteria  
- Final test summary report completed and reviewed  
- All test artifacts archived in the repository  

---

## 10. Risks and Mitigation

| Risk                              | Likelihood | Impact | Priority | Mitigation                                    |
|----------------------------------|------------|--------|----------|-----------------------------------------------|
| Incorrect JSON schema undetected | Medium     | High   | High     | Use JSON Schema validation in Postman         |
| Unexpected error codes on invalid requests | High       | Medium | High     | Design extensive negative test cases          |
| Slow API response times           | Low        | Medium | Medium   | Log response times, flag and retest slow endpoints |
| Data persistence issues after DELETE | Medium     | Low    | Medium   | Retest deletions and resource recreation      |

---

## 11. Deliverables

- Test Plan document (`TestPlan/Reqres_Test_Plan.md`)  
- Test Case Suite (`TestCases/Reqres_API_TC.md`)  
- Test Data JSON files (`TestData/valid_payloads.json`, `invalid_payloads.json`)  
- Execution results logs and response snapshots (`ExecutionResults/`)  
- Defect reports in GitHub Issues  
- Daily Reports (`Reports/Daily_Report_DD-MM-YYYY.md`)  
- Final Summary Report (`Reports/Final_Report.md`)  

---

## 12. Schedule

### Day 0: Folder Setup & Tool Installation

| Activity                                                        | Duration    |
|----------------------------------------------------------------|-------------|
| Create project folder structure (`~/ReqresTesting/`)            | 15 minutes  |
| Install and configure Postman, VS Code, JSON Schema plugin     | 45 minutes  |
| Initialize GitHub repository and set up issue templates        | 30 minutes  |

---

### Day 1: Test Plan & Test Data Preparation

| Activity                                                          | Duration    |
|------------------------------------------------------------------|-------------|
| Write Test Plan document (`TestPlan/Reqres_Test_Plan.md`)         | 2 hour      |
| Prepare valid and invalid JSON payloads in `TestData/`            | 1 hour      |
| Design detailed test cases in `TestCases/Reqres_API_TC.md`  | 4-5 hours   |

---

### Day 2: Execute GET Endpoints

| Activity                                                        | Duration    |
|----------------------------------------------------------------|-------------|
| Run GET /users?page and GET /users/{id} tests in Postman       | 2 hours     |
| Exploratory testing with boundary and invalid parameters       | 1 hour      |
| Log bugs in GitHub Issues                                  | 1 hour      |

---

### Day 3: Execute POST Endpoints

| Activity                                                    | Duration    |
|------------------------------------------------------------|-------------|
| Run POST /register and POST /login test cases              | 2 hours     |
| Exploratory testing with malformed JSON and SQL injection  | 1 hour      |
| Log 3–4 bugs and write daily report                         | 1 hour      |

---

### Day 4: Execute PUT/PATCH and DELETE Endpoints

| Activity                                                    | Duration    |
|------------------------------------------------------------|-------------|
| Run PUT, PATCH, DELETE test cases                           | 2 hours     |
| Exploratory testing for concurrent deletes and invalid IDs | 1 hour      |
| Log 2–3 bugs and write daily report                         | 1 hour      |

---

### Day 5: Execute GET /unknown Endpoints & Bug Retesting

| Activity                                                       | Duration    |
|----------------------------------------------------------------|-------------|
| Run GET /unknown and GET /unknown/{id} test cases              | 2 hour      |
| Exploratory testing on edge cases and response times           | 1 hour      |
| Retest all logged bugs and update issue statuses               | 1 hour      |
| Write daily report and update execution logs                   | 1 hour      |

---

### Day 6: Final Verification and Bug Closure

| Activity                                                      | Duration    |
|---------------------------------------------------------------|-------------|
| Review execution results and screenshots                      | 2 hours     |
| Clean and organize GitHub Issues, assign severities           | 3 hours     |
| Begin drafting final report                                   | 1 hour      |

---

### Day 7: Final Report and Portfolio Preparation

| Activity                                                          | Duration    |
|------------------------------------------------------------------|-------------|
| Complete final report with metrics, analysis, and lessons learned | 2 hours     |
| Update README with project overview and usage instructions        | 2 hour      |
| Prepare response screenshots for portfolio                        | 1 hour      |
| Add project details to CV                                         | 1 hour      |