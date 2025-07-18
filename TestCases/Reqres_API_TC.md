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
- Response time is under 3 seconds.
- Header `Content-Type` is `application/json`.  
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
- Response time is under 3 seconds.
- Header `Content-Type` is `application/json`.  
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
- Response time is under 3 seconds. 
- Header `Content-Type` is `application/json`. 
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
- Status code is either `200 OK` or `400 Bad Request`.  
- If `200`: `"data": []`, and page defaults to 1.  
- If `400`: error JSON includes valid error message.
- Header `Content-Type` is `application/json`.
- Response time is under 3 seconds.

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
- Count of `data[] == per_page`.
- Header `Content-Type` is `application/json`.
- Response time is under 3 seconds.

**Priority:** High  

**Type:** Functional  

---

### API_06  
**Title:** Verify GET /users?page=abc returns error or empty  

**Preconditions:** None  

**Test Steps:**  
1. Send GET request to `https://reqres.in/api/users?page=abc`.  

**Expected Results:**  
- Status code is either `400 Bad Request` or `200 OK`.  
- If `200`: `"data": []` and default `page` value used.  
- If `400`: JSON contains error message like "Invalid page value".
-   Header `Content-Type` is `application/json`.
-   Response time is under 3 seconds.

**Priority:** Medium  

**Type:** Negative  

---

### API_07  
**Title:** Verify GET /users?page=1 pagination metadata present  

**Preconditions:** None  

**Test Steps:**  
1. Send GET request to `https://reqres.in/api/users?page=1`.  
2. Inspect response metadata fields.  

**Expected Results:**  
- Status `200 OK`.  
- Response includes: `page`, `per_page`, `total`, `total_pages`.
- Field types: all integers  
- Values are logically consistent (`page * per_page ≤ total`).
- Header `Content-Type` is `application/json`.
- Response time is under 3 seconds.  

**Priority:** High  

**Type:** Functional  

---

### API_08  
**Title:** Verify GET /users?page=1 supports CORS headers  

**Preconditions:** None  

**Test Steps:**  
1. Send GET request to `https://reqres.in/api/users?page=1`.  
2. Inspect response headers.  

**Expected Results:**  
- Header `Access-Control-Allow-Origin: *` is present.  
- Other standard CORS headers may be present (e.g. `Access-Control-Allow-Methods`).
- Header `Content-Type` is `application/json`.
- Response time is under 3 seconds.   

**Priority:** Low  

**Type:** Boundary  

---

## GET /users/{id} (6 cases)

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
- Response contains fields (`id`, `email`, `first_name`, `last_name`, `avatar`).  
- `data.id` is `2`.  
- Response header Content-Type is application/json.

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
- Response body is `{}` or empty string.  
- No user data is returned.  
- Response header Content-Type is application/json.

**Priority:** High  

**Type:** Negative  

---

### API_11  
**Title:** Verify GET /users/string returns 404 or error  

**Preconditions:** None  

**Test Steps:**  
1. Send GET request to `https://reqres.in/api/users/abc`.  

**Expected Results:**  
- Status code is 404 Not Found or 400 Bad Request depending on API behavior.  
- Response body is `{}` or empty string.  
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
- Response body is `{}` or empty string.  

**Priority:** Medium  

**Type:** Negative  

---

### API_13  
**Title:** Verify GET /users/1 returns expected structure  

**Preconditions:** None  

**Test Steps:**  
1. Send GET request to `https://reqres.in/api/users/1`.
2. Response contains fields (`id`, `email`, `first_name`, `last_name`, `avatar`).   
3. Inspect `data.email`.  
4. Inspect `support.url`.  

**Expected Results:**  
- Status code is `200 OK`.  
- `data.email` contains `@`.  
- `support.url` is present and valid.
- Response header Content-Type is application/json.
- Field support.url is a valid URL.  

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
- Compare full JSON response bodies for equality.
- Response headers and status codes are consistent.

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

---

## POST /login (6 cases)

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

---

## PUT /users/{id} (3 cases)

### API_29  
**Title:** Verify PUT /users/2 full update returns 200 and updated data  

**Preconditions:**  
- Resource with id=2 exists  

**Test Steps:**  
1. Open Postman.  
2. Set method to PUT and URL to `https://reqres.in/api/users/2`.
3. Add header: `x-api-key: reqres-free-v1`.  
4. Set request body to `{"name":"neo","job":"the one"}`.  
5. Send the request.  

**Expected Results:**  
- HTTP status code is `200 OK`.  
- Response body reflects updated `name` and `job`.  
- Response body contains `updatedAt` timestamp.  
- Response header `Content-Type` is `application/json`.  
- Response time is less than 3 seconds.
- Response headers and status codes are consistent.  

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
3. Add header: `x-api-key: reqres-free-v1`.  
4. Set request body to a valid JSON payload (e.g., `{"name":"test","job":"tester"}`).  
5. Send the request.  

**Expected Results:**  
- HTTP status code is `404 Not Found` or `200 OK` with created resource.  
- Behavior is documented in test results.  
- Response header `Content-Type` is `application/json`.  
- Response time is less than 3 seconds.
- Response headers and status codes are consistent.  

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
3. Add header: `x-api-key: reqres-free-v1`.  
4. Set request body to empty JSON `{}`.  
5. Send the request.  

**Expected Results:**  
- HTTP status code is `400 Bad Request`.  
- Response body contains error message indicating bad request.  
- Response header `Content-Type` is `application/json`.  
- Response time is less than 3 seconds.
- Response headers and status codes are consistent.  

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
3. Add header: `Content-Type: application/json` and `x-api-key: reqres-free-v1`.  
4. Set request body to: `{"name":"morpheus"}`.  
5. Send the request.
6. Validate response fields.  

**Expected Results:**  
- HTTP status code is `200 OK`.  
- Response body contains updated `name: "morpheus"`.  
- Existing `job` remains unchanged (if previously set).  
- Response includes `updatedAt` timestamp.  
- Response header `Content-Type` is `application/json; charstet=utf-8`.  
- Response time is under 3 seconds.  

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
3. Headers: `Content-Type: application/json`, `x-api-key: reqres-free-v1`.  
4. Use empty JSON as request body: `{}`.  
5. Send the request.  

**Expected Results:**  
- HTTP status code is `400 Bad Request`.  
- Response body includes an error message like `"Missing data"` or similar.  
- Header `Content-Type` is `application/json`.  
- Response time < 3 seconds.
- No user data is updated.

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
3. Headers: `Content-Type: application/json`, `x-api-key: reqres-free-v1`.    
4. Set request body to a valid payload: `{"name":"ghost"}`.  
5. Send the request.  

**Expected Results:**  
- HTTP status code `404 Not Found` or `204 No Content`.  
- No data should be updated.  
- Response body is empty or includes error message.  
- Response time is under 3 seconds.  

**Priority:** Medium  

**Type:** Negative 

---

## DELETE /users/{id} (3 cases)

### API_35  
**Title:** Verify DELETE /users/2 returns 204 No Content  

**Preconditions:** Verify user existence with GET /users/2 before DELETE  

**Test Steps:**  
1. Open Postman and set method to DELETE.  
2. Set URL to `https://reqres.in/api/users/2`.  
3. Send the request.  

**Expected Results:**  
- HTTP status code is `204 No Content`.  
- Response body is empty.  
- Response headers include Content-Length: 0.
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
- HTTP status code is `404 Not Found`.  
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
- Verify resource existence with GET /unknown/3 before test execution  

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


