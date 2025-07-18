## POST /register (8 cases)

---

### API_15  
**Title:** Verify POST /register with valid data returns 200 and token  

**Preconditions:**  
- None  

**Test Steps:**  
1. Open Postman.  
2. Set method to POST and URL to `https://reqres.in/api/register`.
3. Add header: `x-api-key: reqres-free-v1`.  
4. Set request body to JSON: `{"email":"eve.holt@reqres.in","password":"pistol"}`.  
5. Send the request.  

**Expected Results:**  
- HTTP status code is `200 OK`.  
- Response body contains `id` (integer) and `token` (string).  
- Response header `Content-Type` is `application/json`.  
- Response time is less than 3 seconds.  

**Priority:** High  

**Type:** Functional  

---

### API_16  
**Title:** Verify POST /register without password returns 400 and error  

**Preconditions:**  
- None  

**Test Steps:**  
1. Open Postman.  
2. POST to `/register` with JSON body: `{"email":"sydney@fife"}`.
3. Add header: `x-api-key: reqres-free-v1`.   
4. Send request.  

**Expected Results:**  
- HTTP status code is `400 Bad Request`.  
- Response body contains `{ "error": "Missing password" }`.  
- Response header `Content-Type` is `application/json`.  
- Response time is less than 3 seconds.  

**Priority:** High  

**Type:** Negative  

---

### API_17  
**Title:** Verify POST /register without email returns 400  

**Preconditions:**  
- None  

**Test Steps:**  
1. Open Postman.  
2. POST to `/register` with JSON body: `{"password":"1234"}`.
3. Add header: `x-api-key: reqres-free-v1`.   
4. Send request.  

**Expected Results:**  
- HTTP status code is `400 Bad Request`.
- No `token` or `id`.  
- Response body contains `{ "error": "Missing email or username" }`.  
- Response header `Content-Type` is `application/json`.  
- Response time is less than 3 seconds.  

**Priority:** High  

**Type:** Negative  

---

### API_18  

**Title:** Verify POST /register with extra fields ignores extras  

**Preconditions:**  
- None  

**Test Steps:**  
1. Open Postman.  
2. POST to `/register` with JSON body: `{"email":"eve.holt@reqres.in","password":"pistol","extra":"x"}`.
3. Add header: `x-api-key: reqres-free-v1`.  
4. Send request.  

**Expected Results:**  
- HTTP status code is `200 OK`.  
- Response body contains valid `id` and `token`.  
- Extra field `extra` is ignored and not returned.  
- Response header `Content-Type` is `application/json`.  
- Response time is less than 3 seconds.  

**Priority:** Medium  

**Type:** Boundary  

---

### API_19  
**Title:** Verify POST /register with blank password returns 400  

**Preconditions:**  
- None  

**Test Steps:**  
1. Open Postman.  
2. POST to `/register` with JSON body: `{"email":"eve.holt@reqres.in","password":""}`.
3. Add header: `x-api-key: reqres-free-v1`.  
4. Send request.  

**Expected Results:**  
- HTTP status code is `400 Bad Request`.  
- Response body contains `{ "error": "Missing password" }`.  
- Response header `Content-Type` is `application/json`.  
- Response time is less than 3 seconds.  

**Priority:** Medium  

**Type:** Negative  

---

### API_20  
**Title:** Verify POST /register with invalid email format returns 400  

**Preconditions:**  
- None  

**Test Steps:**  
1. Open Postman.  
2. POST to `/register` with JSON body: `{"email":"not-an-email","password":"pistol"}`.
3. Add header: `x-api-key: reqres-free-v1`.    
4. Send request.  

**Expected Results:**  
- HTTP status code is `400 Bad Request`.  
- Response body contains an error message related to invalid email format.
- `token` is not returned.  
- Response header `Content-Type` is `application/json`.  
- Response time is less than 3 seconds.  

**Priority:** Medium  

**Type:** Negative  

---

### API_21  
**Title:** Verify POST /register large payload handled  

**Preconditions:**  
- None  

**Test Steps:**  
1. Open Postman.  
2. POST to `/register` with large payload: valid payload repeated 100 times.
3. Add header: `x-api-key: reqres-free-v1`.    
4. Send request.  

**Expected Results:**  
- HTTP status code is `200 OK`.  
- Response body contains one valid `token` and `id`.
- Response header `Content-Type` is `application/json`.  
- Response time is less than 3 seconds.  

**Priority:** Low  

**Type:** Boundary  

---

### API_22  
**Title:** Verify POST /register performance under 3s  

**Preconditions:**  
- None  

**Test Steps:**  
1. Open Postman.  
2. POST to `/register` with valid payload.  
3. Measure response time.  

**Expected Results:**   
- HTTP status code is `200 OK`.  
- Response header `Content-Type` is `application/json`.
- Response time is less than 3 seconds.   

**Priority:** Low  

**Type:** Boundary 