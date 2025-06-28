## PUT /users/{id} (3 cases)

### API_29  
**Title:** Verify PUT /users/2 full update returns 200 and updated data  

**Preconditions:**  
- Resource with id=2 exists  

**Test Steps:**  
1. Open Postman.  
2. Set method to PUT and URL to `https://reqres.in/api/users/2`.  
3. Set request body to `{"name":"neo","job":"the one"}`.  
4. Send the request.  

**Expected Results:**  
- HTTP status code is `200 OK`.  
- Response body reflects updated `name` and `job`.  
- Response body contains `updatedAt` timestamp.  
- Response header `Content-Type` is `application/json`.  
- Response time is less than 3 seconds.  

**Priority:** High  

**Type:** Functional 

---

### API_30  
**Title:** Verify PUT /users/999 returns 404 or handles gracefully  

**Preconditions:**  
- Resource with id=999 does not exist  

**Test Steps:**  
1. Open Postman.  
2. Set method to PUT and URL to `https://reqres.in/api/users/999`.  
3. Set request body to a valid JSON payload (e.g., `{"name":"test","job":"tester"}`).  
4. Send the request.  

**Expected Results:**  
- HTTP status code is `404 Not Found` or `200 OK` with created resource.  
- Behavior is documented in test results.  
- Response header `Content-Type` is `application/json`.  
- Response time is less than 3 seconds.  

**Priority:** Medium  

**Type:** Negative

---

### API_31  
**Title:** Verify PUT /users/2 with empty body returns 400  

**Preconditions:**  
- Resource with id=2 exists  

**Test Steps:**  
1. Open Postman.  
2. Set method to PUT and URL to `https://reqres.in/api/users/2`.  
3. Set request body to empty JSON `{}`.  
4. Send the request.  

**Expected Results:**  
- HTTP status code is `400 Bad Request`.  
- Response body contains error message indicating bad request.  
- Response header `Content-Type` is `application/json`.  
- Response time is less than 3 seconds.  

**Priority:** Medium  

**Type:** Negative

---