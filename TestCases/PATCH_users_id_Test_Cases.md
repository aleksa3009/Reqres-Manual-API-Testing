## PATCH /users/{id} (3 cases)

---

### API_32  
**Title:** Verify PATCH /users/2 partial update of name returns 200  

**Preconditions:**  
- User with ID=2 exists  

**Test Steps:**  
1. Open Postman and set method to PATCH.  
2. Set URL to `https://reqres.in/api/users/2`.
3. Add header: `Content-Type: application/json` and `x-api-key: reqres-free-v1`.  
4. Set request body to: `{"name":"morpheus"}`.  
5. Send the request.
6. Validate response fields.  

**Expected Results:**  
- HTTP status code is `200 OK`.  
- Response body contains updated `name: "morpheus"`.  
- Existing `job` remains unchanged (if previously set).  
- Response includes `updatedAt` timestamp.  
- Response header `Content-Type` is `application/json; charstet=utf-8`.  
- Response time is under 3 seconds.  

**Priority:** High  

**Type:** Functional  

---

### API_33  
**Title:** Verify PATCH /users/2 with empty payload returns 400  

**Preconditions:**  
- User with ID=2 exists  

**Test Steps:**  
1. Open Postman and set method to PATCH.  
2. Set URL to `https://reqres.in/api/users/2`.
3. Headers: `Content-Type: application/json`, `x-api-key: reqres-free-v1`.  
4. Use empty JSON as request body: `{}`.  
5. Send the request.  

**Expected Results:**  
- HTTP status code is `400 Bad Request`.  
- Response body includes an error message like `"Missing data"` or similar.  
- Header `Content-Type` is `application/json`.  
- Response time < 3 seconds.
- No user data is updated.

**Priority:** Medium  

**Type:** Negative  

---

### API_34  
**Title:** Verify PATCH /users/999 returns 404 or empty response  

**Preconditions:**  
- User with ID=999 does not exist  

**Test Steps:**  
1. Open Postman and set method to PATCH.  
2. Set URL to `https://reqres.in/api/users/999`.
3. Headers: `Content-Type: application/json`, `x-api-key: reqres-free-v1`.    
4. Set request body to a valid payload: `{"name":"ghost"}`.  
5. Send the request.  

**Expected Results:**  
- HTTP status code `404 Not Found` or `204 No Content`.  
- No data should be updated.  
- Response body is empty or includes error message.  
- Response time is under 3 seconds.  

**Priority:** Medium  

**Type:** Negative 

---