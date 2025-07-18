## POST /login (6 cases)

---

### API_23  
**Title:** Verify POST /login with valid credentials returns 200 and token  

**Preconditions:**  
- None  

**Test Steps:**  
1. Open Postman.  
2. Set method to POST and URL to `https://reqres.in/api/login`.
3. Add header: `x-api-key: reqres-free-v1`.  
4. Set request body to JSON: `{"email":"eve.holt@reqres.in","password":"cityslicka"}`.  
5. Send the request.  

**Expected Results:**  
- HTTP status code is `200 OK`.  
- Response body contains `token` (non-empty string).
- Token is alphanumeric and consistent in format.
- No sensitive data (e.g., password) is returned.  
- `Content-Type` is `application/json`.  
- Response time is less than 3 seconds.  

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
3. Add header: `x-api-key: reqres-free-v1`.
4. Send request.  

**Expected Results:**  
- HTTP status code is `400 Bad Request`.  
- Response body contains `{ "error": "Missing password" }`.
- `"error"` field is present and informative.
- `token` field is not present.
- `Content-Type` is `application/json`.  
- Response time is less than 3 seconds.  

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
3. Add header: `x-api-key: reqres-free-v1`.  
4. Send request.  

**Expected Results:**  
- HTTP status code is `400 Bad Request`.  
- Response body contains `{ "error": "Missing email or username" }`.  
- `"error"` field is present and informative.
- `token` field is not present.
- `Content-Type` is `application/json`.  
- Response time is less than 3 seconds.  

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
3. Add header: x-api-key: reqres-free-v1.
4. Send request.  

**Expected Results:**  
- HTTP status code is `400 Bad Request`.  
- Response body contains error message like: `{ "error": "user not found" }`.  
- `token` field is not present.
- `Content-Type` is `application/json`.  
- Response time is less than 3 seconds. 

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
3. Add header: `x-api-key: reqres-free-v1`.
4. Send request.  

**Expected Results:**  
- HTTP status code is `400 Bad Request`.  
- Response body contains email format error or generic error message.  
- `Content-Type` is `application/json`.  
- Response time is less than 3 seconds.  

**Priority:** Medium  

**Type:** Negative  

---

### API_28  
**Title:** Verify POST /login performance under 3s  

**Preconditions:**  
- None  

**Test Steps:**  
1. Open Postman.  
2. Send valid POST login request: `{"email":"eve.holt@reqres.in","password":"cityslicka"}`. 
3. Add header: `x-api-key: reqres-free-v1`.
4. Measure response duration using Postman.  

**Expected Results:**   
- Status code is `200 OK`.  
- Response contains valid `token`.
- Response time is less than 3000ms. 
- No performance degradation or timeout.

**Priority:** Low  

**Type:** Boundary/Performance 