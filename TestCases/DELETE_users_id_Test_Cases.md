## DELETE /users/{id} (3 cases)

### API_35  
**Title:** Verify DELETE /users/2 returns 204 No Content  
**Preconditions:** Resource 2 exists  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. DELETE `/users/2`.  
3. Status `204`.  
4. No response body.  
**Priority:** High  
**Type:** Functional

### API_36  
**Title:** Verify DELETE /users/2 again returns 404  
**Preconditions:** Resource 2 has been deleted  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. DELETE `/users/2`.  
3. Status `404`.  
4. No data.  
**Priority:** Medium  
**Type:** Negative

### API_37  
**Title:** Verify DELETE /users/abc returns error  
**Preconditions:** None  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. DELETE `/users/abc`.  
3. Status `400` or `404`.  
4. Appropriate error message.  
**Priority:** Medium  
**Type:** Negative

---