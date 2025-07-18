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