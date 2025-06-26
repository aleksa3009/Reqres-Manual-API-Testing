# Daily Report – Day 2 (26-06-2025)

**Tester:** Aleksa Aleksić  
**Project:** Reqres.in API Manual Testing  
**Date:** 26.06.2025

---

## Activities:
- Executed **8** test cases for `GET /users?page={n}` endpoints in Postman.  
- Executed **6** test cases for `GET /users/{id}` endpoints.  
- Recorded PASS/FAIL results in `Module_Results_GetEndpoints.md`.  
- Captured **5** screenshots for failing test cases and saved in `ExecutionResults/Screenshots/`.  
- Logged **5** defects in GitHub Issues with detailed reproduction steps and screenshots.  

## Environment:
- **OS:** Ubuntu 22.04 LTS  
- **API Client:** Postman v10.18.1  
- **Test Management:** Visual Studio Code (Markdown)  
- **Defect Tracking:** GitHub Issues  
- **Time Tracking:** Manual timestamps recorded in execution results file

## Issues:
- **Bug-01:** `GET /users?page=0` returned "error": "Missing API key."  
- **Bug-02:** `GET /users?page=-1` returned status 200 with data instead of error/empty.  
- **Bug-03:** `GET /users?page=abc` returned non-empty data instead of error or empty array.  
- **Bug-04:** `GET /users/23` returned 200 instead of 404.  
- **Bug-05:** `GET /users/0` returned 200 with default user object instead of 404.

## Exploratory Findings:
1. **Delay Parameter Behavior:** Adding `?delay=3` to `GET /users?page=1` delayed response ~3 seconds but still returned full dataset—no timeout or partial response observed.  
2. **Header Handling:** Omitting the `Accept: application/json` header caused the API to default to JSON response, indicating robust default content negotiation.  
3. **Rate Limit Check:** Sending **10** consecutive `GET /users?page=1` requests within 1 minute showed consistent response times and no rate-limiting errors.

## Next Steps:
- Proceed with execution of **POST** endpoints (`/register`, `/login`) on Day 3.  
- Use `valid_payloads.json` and `invalid_payloads.json` for positive and negative test scenarios.  
- Prepare execution results template `Module_Results_PostEndpoints.md`.  
- Continue logging defects in GitHub Issues during test execution.
- Write and submit daily report for 27.06.2025.