# Test Cases: Reqres.in API Manual Testing Suite

## GET /users?page={n} (8 cases)

---

### API_01  
**Title:** Verify GET /users?page=1 returns 200 and valid schema  

**Preconditions:** None  

**Test Steps:**  
1. Open Postman and set method to GET.  
2. Set URL to `https://reqres.in/api/users?page=1`.  
3. Add header `x-api-key: reqres-free-v1`.  
4. Send the request.  
5. Validate JSON structure against schema.  
6. Inspect first item in `data[]`.  

**Expected Results:**  
- Status code is `200 OK`.  
- Response JSON includes `page`, `per_page`, `total`, `total_pages`, `data[]`.  
- Each `data[]` item has `id`, `email`, `first_name`, `last_name`, `avatar`.  

**Priority:** High  

**Type:** Functional  

---

### API_02  
**Title:** Verify GET /users?page=0 returns empty list  

**Preconditions:** None  

**Test Steps:**  
1. Send GET request to `https://reqres.in/api/users?page=0`.  

**Expected Results:**  
- Status code `200 OK`.  
- Response contains `"data": []`.  
- Field `"page"` equals `0`.  

**Priority:** Medium  

**Type:** Negative  

---

### API_03  
**Title:** Verify GET /users?page=100 returns empty data  

**Preconditions:** None  

**Test Steps:**  
1. Send GET request to `https://reqres.in/api/users?page=100`.  

**Expected Results:**  
- Status `200 OK`.  
- Response includes `"data": []`.  
- Field `total_pages` remains unchanged.  

**Priority:** Medium  

**Type:** Negative  

---

### API_04  
**Title:** Verify GET /users?page=-1 handles invalid page  

**Preconditions:** None  

**Test Steps:**  
1. Send GET request to `https://reqres.in/api/users?page=-1`.  
**Expected Results:**  
- Status `200 OK` or `400 Bad Request`.  
- If `200`: `"data": []` expected.  
- If `400`: error JSON with proper message.  

**Priority:** Medium  

**Type:** Negative  

---

### API_05  
**Title:** Verify GET /users?page=1 returns correct `per_page` count  

**Preconditions:** None  

**Test Steps:**  
1. Send GET request to `https://reqres.in/api/users?page=1`.  
2. Extract `per_page` value.  
3. Count elements in `data[]`.  

**Expected Results:**  
- Status `200 OK`.  
- Count of `data[]` equals `per_page`.  

**Priority:** High  

**Type:** Functional  

---

### API_06  
**Title:** Verify GET /users?page=abc returns error or empty  

**Preconditions:** None  

**Test Steps:**  
1. Send GET request to `https://reqres.in/api/users?page=abc`.  

**Expected Results:**  
- Status `400` or `200`.  
- If `200`: `"data": []`.  
- If `400`: JSON contains error message.  

**Priority:** Medium  

**Type:** Negative  

---

### API_07  
**Title:** Verify GET /users?page=1 pagination metadata present  

**Preconditions:** None  

**Test Steps:**  
1. Send GET request to `https://reqres.in/api/users?page=1`.  
2. Inspect response fields.  

**Expected Results:**  
- Status `200 OK`.  
- Fields present: `page`, `per_page`, `total`, `total_pages`.  
- Values are logically consistent.  

**Priority:** High  

**Type:** Functional  

---

### API_08  
**Title:** Verify GET /users?page=1 supports CORS headers  

**Preconditions:** None  

**Test Steps:**  
1. Send GET request to `https://reqres.in/api/users?page=1`.  
2. Check response headers.  

**Expected Results:**  
- Header `Access-Control-Allow-Origin: *` is present.  
- Other standard CORS headers (e.g. `Access-Control-Allow-Methods`) exist.  

**Priority:** Low  

**Type:** Boundary  

---

### API_09  
**Title:** Verify GET /users/2 returns 200 and correct user  

**Preconditions:** None  

**Test Steps:**  
1. Open Postman and set method to GET.  
2. Send request to `https://reqres.in/api/users/2`.  
3. Validate response schema for single user.  
4. Confirm that `data.id = 2`.  

**Expected Results:**  
- Status code is `200 OK`.  
- Response contains expected user fields (`id`, `email`, `first_name`, etc.).  
- `data.id` is `2`.  

**Priority:** High  

**Type:** Functional  

---

### API_10  
**Title:** Verify GET /users/23 returns 404  

**Preconditions:** None  

**Test Steps:**  
1. Send GET request to `https://reqres.in/api/users/23`.  

**Expected Results:**  
- Status code is `404 Not Found`.  
- Response body is empty or `{}`.  
- No user data is returned.  

**Priority:** High  

**Type:** Negative  

---

### API_11  
**Title:** Verify GET /users/string returns 404 or error  

**Preconditions:** None  

**Test Steps:**  
1. Send GET request to `https://reqres.in/api/users/abc`.  

**Expected Results:**  
- Status code is `404 Not Found`.  
- Response body is empty.  
- No data structure is returned.  

**Priority:** Medium  

**Type:** Negative  

---

### API_12  
**Title:** Verify GET /users/0 returns 404  

**Preconditions:** None  

**Test Steps:**  
1. Send GET request to `https://reqres.in/api/users/0`.  

**Expected Results:**  
- Status code is `404 Not Found`.  
- Response body is empty or `{}`.  

**Priority:** Medium  

**Type:** Negative  

---

### API_13  
**Title:** Verify GET /users/1 returns expected structure  

**Preconditions:** None  

**Test Steps:**  
1. Send GET request to `https://reqres.in/api/users/1`.  
2. Inspect `data.email`.  
3. Inspect `support.url`.  

**Expected Results:**  
- Status code is `200 OK`.  
- `data.email` contains `@`.  
- `support.url` is present and valid.  

**Priority:** High  

**Type:** Functional  

---

### API_14  
**Title:** Verify GET /users/2 repeated calls return consistent data  

**Preconditions:** None  

**Test Steps:**  
1. Send GET request to `/users/2`.  
2. Repeat request.  
3. Compare both responses.  

**Expected Results:**  
- Status `200 OK` on both requests.  
- Response bodies are identical (same `id`, `email`, etc.).  

**Priority:** Low  

**Type:** Boundary  

---

## POST /register (8 cases)

### API_15  
**Title:** Verify POST /register with valid data returns 200 and token  

**Preconditions:**  
- None  

**Test Steps:**  
1. Open Postman.  
2. Set method to POST and URL to `https://reqres.in/api/register`.  
3. Set request body to JSON: `{"email":"eve.holt@reqres.in","password":"pistol"}`.  
4. Send the request.  

**Expected Results:**  
- HTTP status code `200 OK`.  
- Response body contains `id` (integer) and `token` (string).  
- Response header `Content-Type` is `application/json`.  
- Response time less than 3 seconds.  

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
3. Send request.  

**Expected Results:**  
- HTTP status code `400 Bad Request`.  
- Response body contains `{ "error": "Missing password" }`.  
- Response header `Content-Type` is `application/json`.  
- Response time less than 3 seconds.  

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
3. Send request.  

**Expected Results:**  
- HTTP status code `400 Bad Request`.  
- Response body contains `{ "error": "Missing email or username" }`.  
- Response header `Content-Type` is `application/json`.  
- Response time less than 3 seconds.  

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
3. Send request.  

**Expected Results:**  
- HTTP status code `200 OK`.  
- Response body contains valid `id` and `token`.  
- Extra field `extra` is ignored and not returned.  
- Response header `Content-Type` is `application/json`.  
- Response time less than 3 seconds.  

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
3. Send request.  

**Expected Results:**  
- HTTP status code `400 Bad Request`.  
- Response body contains `{ "error": "Missing password" }`.  
- Response header `Content-Type` is `application/json`.  
- Response time less than 3 seconds.  

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
3. Send request.  

**Expected Results:**  
- HTTP status code `400 Bad Request`.  
- Response body contains an error message related to invalid email format.  
- Response header `Content-Type` is `application/json`.  
- Response time less than 3 seconds.  

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
3. Send request.  

**Expected Results:**  
- HTTP status code `200 OK`.  
- Response body contains one valid `token`.  
- Response header `Content-Type` is `application/json`.  
- Response time less than 3 seconds.  

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
- Response time is less than 3000 milliseconds (3 seconds).  
- HTTP status code `200 OK`.  
- Response header `Content-Type` is `application/json`.  

**Priority:** Low  

**Type:** Boundary 

---

## POST /login (6 cases)

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

---

## PUT /users/{id} (3 cases)

### API_29  
**Title:** Verify PUT /users/2 full update returns 200 and updated data  

**Preconditions:**  
- Resource with id=2 exists  

**Test Steps:**  
1. Open Postman.  
2. Set method to PUT and URL to `https://reqres.in/api/users/2`.  
3. Set request body to `{"name":"neo","job":"the one"}`.  
4. Send the request.  

**Expected Results:**  
- HTTP status code is `200 OK`.  
- Response body reflects updated `name` and `job`.  
- Response body contains `updatedAt` timestamp.  
- Response header `Content-Type` is `application/json`.  
- Response time is less than 3 seconds.  

**Priority:** High  

**Type:** Functional 

---

### API_30  
**Title:** Verify PUT /users/999 returns 404 or handles gracefully  

**Preconditions:**  
- Resource with id=999 does not exist  

**Test Steps:**  
1. Open Postman.  
2. Set method to PUT and URL to `https://reqres.in/api/users/999`.  
3. Set request body to a valid JSON payload (e.g., `{"name":"test","job":"tester"}`).  
4. Send the request.  

**Expected Results:**  
- HTTP status code is `404 Not Found` or `200 OK` with created resource.  
- Behavior is documented in test results.  
- Response header `Content-Type` is `application/json`.  
- Response time is less than 3 seconds.  

**Priority:** Medium  

**Type:** Negative

---

### API_31  
**Title:** Verify PUT /users/2 with empty body returns 400  

**Preconditions:**  
- Resource with id=2 exists  

**Test Steps:**  
1. Open Postman.  
2. Set method to PUT and URL to `https://reqres.in/api/users/2`.  
3. Set request body to empty JSON `{}`.  
4. Send the request.  

**Expected Results:**  
- HTTP status code is `400 Bad Request`.  
- Response body contains error message indicating bad request.  
- Response header `Content-Type` is `application/json`.  
- Response time is less than 3 seconds.  

**Priority:** Medium  

**Type:** Negative

---

## PATCH /users/{id} (3 cases)

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

## DELETE /users/{id} (3 cases)

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

## GET /unknown/{id} (3 cases)

### API_38  
**Title:** Verify GET /unknown returns metadata list 200  

**Preconditions:**  
- None  

**Test Steps:**  
1. Open Postman.  
2. Set method to GET and URL to `https://reqres.in/api/unknown`.  
3. Send the request.  

**Expected Results:**  
- HTTP status code `200 OK`.  
- Response body contains `data[]` array with resource metadata fields: `id`, `name`, `year`, `color`, `pantone_value`.  
- Response header `Content-Type` is `application/json`.  
- Response time is less than 3 seconds.  

**Priority:** High  

**Type:** Functional 

---

### API_39  
**Title:** Verify GET /unknown/3 returns 200 and correct resource

**Preconditions:**  
- Resource with id=3 exists  

**Test Steps:**  
1. Open Postman.  
2. Set method to GET and URL to `https://reqres.in/api/unknown/3`.  
3. Send the request.  

**Expected Results:**  
- HTTP status code `200 OK`.  
- Response body contains `data.id` equal to `3`.  
- Response body includes correct `name`, `year`, `color`, and `pantone_value` fields.  
- Response header `Content-Type` is `application/json`.  
- Response time is less than 3 seconds.
-   
**Priority:** High  

**Type:** Functional 

---

### API_40  
**Title:** Verify GET /unknown/23 returns 404  

**Preconditions:**  
- Resource with id=23 does not exist 
   
**Test Steps:**  
1. Open Postman.  
2. Set method to GET and URL to `https://reqres.in/api/unknown/23`.  
3. Send the request.  
   
**Expected Results:**  
- HTTP status code `404 Not Found`.  
- Response body is empty or contains appropriate error message.  
- Response header `Content-Type` is `application/json`.  
- Response time is less than 3 seconds.  

**Priority:** Medium  

**Type:** Negative  

---


