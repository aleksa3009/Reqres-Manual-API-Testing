## PATCH /users/{id} (3 cases)

### API_32  
**Title:** Verify PATCH /users/2 partial update of name returns 200  
**Preconditions:** Resource 2 exists  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. PATCH `/users/2` with `{"name":"morpheus"}`.  
3. Status `200`.  
4. Body shows updated `name`, unchanged `job`, and `updatedAt`.  
**Priority:** High  
**Type:** Functional

### API_33  
**Title:** Verify PATCH /users/2 with empty payload returns 400  
**Preconditions:** Resource 2 exists  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. PATCH `/users/2` with `{}`.  
3. Status `400`.  
4. Error message indicating bad request.  
**Priority:** Medium  
**Type:** Negative

### API_34  
**Title:** Verify PATCH /users/999 returns 404 or empty response  
**Preconditions:** Resource 999 does not exist  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. PATCH `/users/999` with valid payload.  
3. Status `404` or similar.  
4. No data updated.  
**Priority:** Medium  
**Type:** Negative

---