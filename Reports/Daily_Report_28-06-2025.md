# Daily Report – Day 4 (27-06-2025)

**Tester:** Aleksa Aleksić  
**Project:** Reqres.in API Manual Testing  
**Date:** 28.06.2025

---

## Activities:
- Executed **12** test cases for `PUT /users/{id}`, `PATCH /users/{id}`, `DELETE /users/{id}` and `GET /unknown/{id}` endpoints in Postman.  
- Recorded PASS/FAIL results in `Module_Results_PUT_Endpoints.md`, `Module_Results_PATCH_Endpoints.md`, `Module_Results_DELETE_Endpoints.md` and `Module_Results_GET_unknown_Endpoints.md`.  
- Captured **4** screenshots for failing test cases and saved in `ExecutionResults/Screenshots/`.  
- Logged **4** defects in GitHub Issues with detailed reproduction steps and screenshots.  
- Performed **3** exploratory tests with malformed JSON.
- Retested all defects and write daily report  

## Environment:
- **OS:** Ubuntu 22.04 LTS  
- **API Client:** Postman v11.49.3  
- **Test Management:** Visual Studio Code (Markdown)  
- **Defect Tracking:** GitHub Issues  
- **Time Tracking:** Manual timestamps recorded in execution results file

## Issues:
- **Bug-01:** `PUT /users/999` returns 200 instead of 404 (API_30).  
- **Bug-02:** `PUT /users2` with empty body returns 200 instead of 400 (API_31).  
- **Bug-03:** `POST /login` with empty payload returns 200 instead of 400 (API_33). 
- **Bug-04:** `DELETE /users/2` again returns 200 instead of 404   (API_36)

## Exploratory Findings  
1.**Malformed JSON Payloads:** Sending malformed JSON (missing commas, brackets) results in `400 Bad Request` errors as expected, confirming proper input validation.    
2.**Multiple Rapid DELETE Requests:** Performing two or more rapid DELETE requests on the same user ID always returns `204 No Content`, suggesting the API is idempotent but fails to reflect resource deletion with a `404` on second call.  
3.**Unexpected Data Types:** Sending integers for `name` or boolean values in `job` fields (e.g. `{"name":123, "job":true}`) is accepted with `200 OK`, indicating possible lack of server-side schema validation.  

## Next Steps
- Review all execution result files for completeness.  
- Draft Final Report with metrics and lessons learned.  
- Prepare screenshots and sample payloads for portfolio.
- Write README.md
- Finish project
