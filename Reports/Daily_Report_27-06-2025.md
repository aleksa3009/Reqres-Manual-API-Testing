# Daily Report – Day 3 (27-06-2025)

**Tester:** Aleksa Aleksić  
**Project:** Reqres.in API Manual Testing  
**Date:** 27.06.2025

---

## Activities:
- Executed **14** test cases for `POST /register` and `POST /login` endpoints in Postman.  
- Recorded PASS/FAIL results in `Module_Results_POST_Endpoints.md`.  
- Captured **3** screenshots for failing test cases and saved in `ExecutionResults/Screenshots/`.  
- Logged **3** defects in GitHub Issues with detailed reproduction steps and screenshots.  
- Performed **2** exploratory tests with malformed JSON and SQL injection payloads.  

## Environment:
- **OS:** Ubuntu 22.04 LTS  
- **API Client:** Postman v10.18.1  
- **Test Management:** Visual Studio Code (Markdown)  
- **Defect Tracking:** GitHub Issues  
- **Time Tracking:** Manual timestamps recorded in execution results file

## Issues:
- **Bug-01:** `POST /register` without password returns 200 instead of 400 with error (API_16).  
- **Bug-02:** `POST /register` with blank password returns 200 instead of 400 with error (API_19).  
- **Bug-03:** `POST /login` without password returns 200 instead of 400 with error (API_24).  

## Exploratory Findings:
1. **Malformed JSON Payloads:** Sending malformed JSON (missing commas, brackets) results in `400 Bad Request` errors as expected, confirming proper input validation.  
2. **SQL Injection Attempts:** SQL-like payloads in email and password fields do not cause errors or leaks; API safely returns `400` or error messages without backend crashes or data exposure.  

## Next Steps:
- Continue with in-depth boundary and negative tests on POST endpoints.  
- Start preparation of full test report document for submission.  
- Investigate adding automation scripts for repetitive payload testing.  
- Plan exploratory tests for other endpoints like PUT and DELETE if available.
