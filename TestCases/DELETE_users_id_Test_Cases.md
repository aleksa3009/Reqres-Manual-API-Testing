## DELETE /users/{id} (3 cases)

---

### API_35  
**Title:** Verify DELETE /users/2 returns 204 No Content  

**Preconditions:** User with ID=2 exists  

**Test Steps:**  
1. Open Postman and set method to DELETE.  
2. Set URL to `https://reqres.in/api/users/2`.  
3. Send the request.  

**Expected Results:**  
- HTTP status code is `204 No Content`.  
- Response body is empty.  
- Response time is under 3 seconds.  

**Priority:** High  

**Type:** Functional  

---

### API_36  
**Title:** Verify DELETE /users/2 again returns 404  

**Preconditions:** User with ID=2 has already been deleted  

**Test Steps:**  
1. Send DELETE request to `https://reqres.in/api/users/2`.  

**Expected Results:**  
- HTTP status code is `404 Not Found` or similar.  
- Response body is empty or contains appropriate error.  

**Priority:** Medium  

**Type:** Negative  

---

### API_37  
**Title:** Verify DELETE /users/abc returns error  

**Preconditions:** None  

**Test Steps:**  
1. Send DELETE request to `https://reqres.in/api/users/abc`.  

**Expected Results:**  
- HTTP status code is `400 Bad Request` or `404 Not Found`.  
- Response contains an appropriate error message.  

**Priority:** Medium  

**Type:** Negative  

---