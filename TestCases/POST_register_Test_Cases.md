## POST /register (8 cases)

### API_15  
**Title:** Verify POST /register with valid data returns 200 and token  
**Preconditions:** None  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. Send POST to `/register` with payload `{"email":"eve.holt@reqres.in","password":"pistol"}`.  
3. Response status `200`.  
4. Body contains `id` (int) and `token` (string).  
**Priority:** High  
**Type:** Functional

### API_16  
**Title:** Verify POST /register without password returns 400 and error  
**Preconditions:** None  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. POST `/register` with `{"email":"sydney@fife"}`.  
3. Status `400`.  
4. Body `{ "error": "Missing password" }`.  
**Priority:** High  
**Type:** Negative

### API_17  
**Title:** Verify POST /register without email returns 400  
**Preconditions:** None  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. POST with `{"password":"1234"}`.  
3. Status `400`.  
4. Body `{ "error": "Missing email or username" }`.  
**Priority:** High  
**Type:** Negative

### API_18  
**Title:** Verify POST /register with extra fields ignores extras  
**Preconditions:** None  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. POST with `{"email":"eve.holt@reqres.in","password":"pistol","extra":"x"}`.  
3. Status `200`.  
4. Response contains `id` and `token`; extra ignored.  
**Priority:** Medium  
**Type:** Boundary

### API_19  
**Title:** Verify POST /register with blank password returns 400  
**Preconditions:** None  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. POST with `{"email":"eve.holt@reqres.in","password":""}`.  
3. Status `400`.  
4. Body `{ "error": "Missing password" }`.  
**Priority:** Medium  
**Type:** Negative

### API_20  
**Title:** Verify POST /register with invalid email format returns 400  
**Preconditions:** None  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. POST with `{"email":"not-an-email","password":"pistol"}`.  
3. Status `400`.  
4. Body error message regarding email.  
**Priority:** Medium  
**Type:** Negative

### API_21  
**Title:** Verify POST /register large payload handled  
**Preconditions:** None  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. POST with same valid payload repeated 100×.  
3. Status `200`.  
4. Token returned only once.  
**Priority:** Low  
**Type:** Boundary

### API_22  
**Title:** Verify POST /register performance under 3s  
**Preconditions:** None  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. POST valid payload.  
3. Measure response time.  
4. Time < 3000ms.  
**Priority:** Low  
**Type:** Boundary

---