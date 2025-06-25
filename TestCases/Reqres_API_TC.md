# Test Cases: Reqres.in API Manual Testing Suite

## GET /users?page={n} (8 cases)

### API_01  
**Title:** Verify GET /users?page=1 returns 200 and valid schema  
**Preconditions:** None  
**Test Steps & Expected Results:**  
1. **Step:** Open Postman.  
   **Expected:** Postman is launched.  
2. **Step:** Send GET `https://reqres.in/api/users?page=1`.  
   **Expected:** Response status `200`.  
3. **Step:** Validate response JSON against user-list schema.  
   **Expected:** Schema matches: root contains `page`, `per_page`, `total`, `total_pages`, `data[]`.  
4. **Step:** Inspect first item in `data[]`.  
   **Expected:** Contains `id`, `email`, `first_name`, `last_name`, `avatar`.  
**Priority:** High  
**Type:** Functional

### API_02  
**Title:** Verify GET /users?page=0 returns empty list  
**Preconditions:** None  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. GET `...?page=0` → status `200`.  
3. Check `data` array → empty (`[].`).  
4. Verify `page` field equals `0`.  
**Priority:** Medium  
**Type:** Negative

### API_03  
**Title:** Verify GET /users?page=100 returns empty data  
**Preconditions:** None  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. GET `...?page=100` → status `200`.  
3. Confirm `data` is empty.  
4. Confirm `total_pages` remains unchanged.  
**Priority:** Medium  
**Type:** Negative

### API_04  
**Title:** Verify GET /users?page=-1 handles invalid page  
**Preconditions:** None  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. GET `...?page=-1` → status `200` or `400`.  
3. If `200`: `data` empty; if `400`: error JSON.  
4. Verify error message if present.  
**Priority:** Medium  
**Type:** Negative

### API_05  
**Title:** Verify GET /users?page=1 returns correct `per_page` count  
**Preconditions:** None  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. GET `...?page=1` → status `200`.  
3. Read `per_page` value → expected `6`.  
4. Count elements in `data` → equals `per_page`.  
**Priority:** High  
**Type:** Functional

### API_06  
**Title:** Verify GET /users?page=abc returns error or empty  
**Preconditions:** None  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. GET `...?page=abc` → status `400` or `200`.  
3. If `200`: `data` empty; if `400`: error JSON.  
4. Confirm appropriate error message.  
**Priority:** Medium  
**Type:** Negative

### API_07  
**Title:** Verify GET /users?page=1 pagination metadata present  
**Preconditions:** None  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. GET `...?page=1` → status `200`.  
3. Verify presence of `page`, `total`, `total_pages`, `per_page`.  
4. Values plausible (e.g. `total_pages` > 0).  
**Priority:** High  
**Type:** Functional

### API_08  
**Title:** Verify GET /users?page=1 supports CORS headers  
**Preconditions:** None  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. GET `...?page=1` → status `200`.  
3. Check response headers → `Access-Control-Allow-Origin: *`.  
4. Confirm other CORS headers exist.  
**Priority:** Low  
**Type:** Boundary

---

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

## PUT /users/{id} (3 cases)

### API_29  
**Title:** Verify PUT /users/2 full update returns 200 and updated data  
**Preconditions:** Resource with id=2 exists  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. PUT `/users/2` with `{"name":"neo","job":"the one"}`.  
3. Status `200`.  
4. Body reflects `name` and `job` updated, contains `updatedAt`.  
**Priority:** High  
**Type:** Functional

### API_30  
**Title:** Verify PUT /users/999 returns 404 or handles gracefully  
**Preconditions:** Resource 999 does not exist  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. PUT `/users/999` with valid payload.  
3. Status `404` or `200` with created resource.  
4. Verify behavior documented.  
**Priority:** Medium  
**Type:** Negative

### API_31  
**Title:** Verify PUT /users/2 with empty body returns 400  
**Preconditions:** Resource 2 exists  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. PUT `/users/2` with `{}`.  
3. Status `400`.  
4. Error message present.  
**Priority:** Medium  
**Type:** Negative

---

