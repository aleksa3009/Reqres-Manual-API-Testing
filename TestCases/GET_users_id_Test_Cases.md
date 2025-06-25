## GET /users/{id} (6 cases)

### API_09  
**Title:** Verify GET /users/2 returns 200 and correct user  
**Preconditions:** None  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. GET `https://reqres.in/api/users/2` → status `200`.  
3. Validate JSON schema for single user.  
4. Confirm `data.id = 2`.  
**Priority:** High  
**Type:** Functional

### API_10  
**Title:** Verify GET /users/23 returns 404  
**Preconditions:** None  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. GET `...?users/23` → status `404`.  
3. Response body empty or `{}`.  
4. No user data present.  
**Priority:** High  
**Type:** Negative

### API_11  
**Title:** Verify GET /users/string returns 404 or error  
**Preconditions:** None  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. GET `...?users/abc` → status `404`.  
3. Response empty.  
4. Confirm no data.  
**Priority:** Medium  
**Type:** Negative

### API_12  
**Title:** Verify GET /users/0 returns 404  
**Preconditions:** None  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. GET `...?users/0` → status `404`.  
3. Response empty.  
4. Confirm no data.  
**Priority:** Medium  
**Type:** Negative

### API_13  
**Title:** Verify GET /users/1 returns expected structure  
**Preconditions:** None  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. GET `...?users/1` → status `200`.  
3. Confirm `data.email` contains `@`.  
4. Confirm `support.url` present.  
**Priority:** High  
**Type:** Functional

### API_14  
**Title:** Verify GET /users/2 repeated calls return consistent data  
**Preconditions:** None  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. GET `/users/2` twice.  
3. Compare both responses.  
4. Data identical (id, email, names).  
**Priority:** Low  
**Type:** Boundary

---