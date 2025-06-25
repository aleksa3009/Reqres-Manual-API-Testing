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