## PATCH /users/{id} (3 cases)

---

### API_32  
**Title:** Verify PATCH /users/2 partial update of name returns 200  

**Preconditions:**  
- User with ID=2 exists  

**Test Steps:**  
1. Open Postman and set method to PATCH.  
2. Set URL to `https://reqres.in/api/users/2`.  
3. Set request body to: `{"name":"morpheus"}`.  
4. Send the request.  

**Expected Results:**  
- HTTP status code `200 OK`.  
- Response body contains updated `name`.  
- Existing `job` remains unchanged (if previously set).  
- Response includes `updatedAt` timestamp.  
- Response header `Content-Type` is `application/json`.  
- Response time < 3 seconds.  

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
3. Use empty JSON as request body: `{}`.  
4. Send the request.  

**Expected Results:**  
- HTTP status code `400 Bad Request`.  
- Response body contains an error message such as `"Missing data"` or similar.  
- `Content-Type` is `application/json`.  
- Response time < 3 seconds.  

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
3. Set request body to a valid payload: `{"name":"ghost"}`.  
4. Send the request.  

**Expected Results:**  
- HTTP status code `404 Not Found` or `204 No Content`.  
- No data should be updated.  
- Response body is empty or includes error message.  
- Response time < 3 seconds.  

**Priority:** Medium  

**Type:** Negative 

---