# Daily Report – Day 0 (24-06-2025)

**Activities:**  
- Completed the Test Plan (`TestPlan/Reqres_Test_Plan.md`), covering introduction, scope, objectives, roles & responsibilities, environment & tools, entry/exit criteria, risk assessment, deliverables and schedule.  
- Prepared test data JSON files in the `TestData/` folder:  
  - `valid_payloads.json` (register, login, full & partial update payloads)  
  - `invalid_payloads.json` (missing fields, extra fields, empty payload)  
- Designed and documented 40 detailed test cases in TestRail (grouped by endpoint: GET /users?page, GET /users/{id}, POST /register, POST /login, PUT/PATCH/DELETE /users/{id}, GET /unknown/{id}).  
- Set up and configured testing tools: Postman environment, TestRail project, GitHub Issues templates, VS Code workspace.  

**Environment:**  
- Operating System: Ubuntu 22.04 LTS  
- API Client: Postman (with JSON Schema plugin)  
- Defect Tracking: GitHub Issues  
- Editor: Visual Studio Code  

**Issues:**  
- No significant issues or blockers encountered during planning, test data preparation, or test case design.
- No blockers encountered. All initial setup tasks completed as planned.  

**Next Steps:**  
- Execute GET endpoint tests (`/users?page={n}` and `/users/{id}`) in Postman and record status codes, response bodies, JSON schema validation, and response times.  
- Perform exploratory variations on edge parameters (invalid page values, non-numeric IDs).  
- Log any defects discovered into GitHub Issues with clear reproduction steps and screenshots.  
- Prepare and submit Daily Report – Day 1.  
