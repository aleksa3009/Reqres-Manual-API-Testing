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