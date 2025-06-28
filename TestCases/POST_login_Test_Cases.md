## POST /login (6 cases)

---

### API_23  
**Title:** Verify POST /login with valid credentials returns 200 and token  

**Preconditions:**  
- None  

**Test Steps:**  
1. Open Postman.  
2. Set method to POST and URL to `https://reqres.in/api/login`.  
3. Set request body to JSON: `{"email":"eve.holt@reqres.in","password":"cityslicka"}`.  
4. Send the request.  

**Expected Results:**  
- HTTP status code `200 OK`.  
- Response body contains `token` (string).  
- Response header `Content-Type` is `application/json`.  
- Response time less than 3 seconds.  

**Priority:** High  

**Type:** Functional  

---

### API_24  
**Title:** Verify POST /login without password returns 400  

**Preconditions:**  
- None  

**Test Steps:**  
1. Open Postman.  
2. Set POST request to `/login` with body: `{"email":"eve.holt@reqres.in"}`.  
3. Send request.  

**Expected Results:**  
- HTTP status code `400 Bad Request`.  
- Response body contains `{ "error": "Missing password" }`.  
- Response header `Content-Type` is `application/json`.  
- Response time less than 3 seconds.  

**Priority:** High  

**Type:** Negative  

---

### API_25  
**Title:** Verify POST /login without email returns 400  

**Preconditions:**  
- None  

**Test Steps:**  
1. Open Postman.  
2. Set POST request to `/login` with body: `{"password":"cityslicka"}`.  
3. Send request.  

**Expected Results:**  
- HTTP status code `400 Bad Request`.  
- Response body contains `{ "error": "Missing email or username" }`.  
- Response header `Content-Type` is `application/json`.  
- Response time less than 3 seconds.  

**Priority:** High  

**Type:** Negative  

---

### API_26  
**Title:** Verify POST /login wrong password returns 400  

**Preconditions:**  
- None  

**Test Steps:**  
1. Open Postman.  
2. Send POST request with: `{"email":"eve.holt@reqres.in","password":"wrong"}`.  
3. Send request.  

**Expected Results:**  
- HTTP status code `400 Bad Request`.  
- Response body contains error like `{ "error": "user not found" }`.  
- Response header `Content-Type` is `application/json`.  
- Response time less than 3 seconds.  

**Priority:** Medium  

**Type:** Negative  

---

### API_27  
**Title:** Verify POST /login invalid email format returns 400  

**Preconditions:**  
- None  

**Test Steps:**  
1. Open Postman.  
2. Send POST request with: `{"email":"bademail","password":"cityslicka"}`.  
3. Send request.  

**Expected Results:**  
- HTTP status code `400 Bad Request`.  
- Response body contains email format error or generic error message.  
- Response header `Content-Type` is `application/json`.  
- Response time less than 3 seconds.  

**Priority:** Medium  

**Type:** Negative  

---

### API_28  
**Title:** Verify POST /login performance under 3s  

**Preconditions:**  
- None  

**Test Steps:**  
1. Open Postman.  
2. Send valid POST login request.  
3. Measure response duration using Postman.  

**Expected Results:**  
- Response time is less than 3000ms.  
- Status code is `200 OK`.  
- Response contains valid `token`.  

**Priority:** Low  

**Type:** Boundary 