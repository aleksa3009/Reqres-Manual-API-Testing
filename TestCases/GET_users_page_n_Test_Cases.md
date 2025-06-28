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
