## POST /login (6 cases)

### API_23  
**Title:** Verify POST /login with valid credentials returns 200 and token  
**Preconditions:** None  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. POST `/login` with `{"email":"eve.holt@reqres.in","password":"cityslicka"}`.  
3. Status `200`.  
4. Body contains `token`.  
**Priority:** High  
**Type:** Functional

### API_24  
**Title:** Verify POST /login without password returns 400  
**Preconditions:** None  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. POST with `{"email":"eve.holt@reqres.in"}`.  
3. Status `400`.  
4. Body `{ "error": "Missing password" }`.  
**Priority:** High  
**Type:** Negative

### API_25  
**Title:** Verify POST /login without email returns 400  
**Preconditions:** None  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. POST with `{"password":"cityslicka"}`.  
3. Status `400`.  
4. Body `{ "error": "Missing email or username" }`.  
**Priority:** High  
**Type:** Negative

### API_26  
**Title:** Verify POST /login wrong password returns 400  
**Preconditions:** None  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. POST `{"email":"eve.holt@reqres.in","password":"wrong"}`.  
3. Status `400`.  
4. Body `{ "error": "user not found" }` or similar.  
**Priority:** Medium  
**Type:** Negative

### API_27  
**Title:** Verify POST /login invalid email format returns 400  
**Preconditions:** None  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. POST `{"email":"bademail","password":"cityslicka"}`.  
3. Status `400`.  
4. Body error.  
**Priority:** Medium  
**Type:** Negative

### API_28  
**Title:** Verify POST /login performance under 3s  
**Preconditions:** None  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. POST valid login.  
3. Measure response time.  
4. Time < 3000ms.  
**Priority:** Low  
**Type:** Boundary

---