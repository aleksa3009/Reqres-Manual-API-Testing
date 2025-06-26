# ExecutionResults/Module_Results_GetEndpoints.md

## GET Endpoint Test Execution (Postman)

**Client:** Postman v10.18.1  
**Environment:** Ubuntu 22.04 LTS  

---

### API_01 – Verify GET /users?page=1 returns 200 and valid schema
**Start Time:** 26-06-2025 10:00  
**Steps:**
1. Open Postman.  
2. Send GET request to `/users?page=1`.  
3. Validate JSON schema.  
4. Inspect `data[]` fields.  
**Result:** PASS  
**End Time:** 26-06-2025 10:05

---

### API_02 – Verify GET /users?page=0 returns empty list
**Start Time:** 26-06-2025 10:06  
**Steps:**
1. Open Postman.  
2. Send GET request to `/users?page=0`.  
3. Check `data[]`.  
4. Verify `page` field equals `0`.  
**Result:** FAIL  
**Actual:** Returned non-empty list instead of empty `data[]`.  
**Screenshot:** `ExecutionResults/Screenshots/API_02_fail.png`  
**End Time:** 26-06-2025 10:14

---

### API_03 – Verify GET /users?page=100 returns empty data
**Start Time:** 26-06-2025 10:16  
**Steps:**
1. Open Postman.  
2. Send GET request to `/users?page=100`.  
3. Confirm `data[]` is empty.  
4. Confirm `total_pages` unchanged.  
**Result:** PASS  
**End Time:** 26-06-2025 10:25

---

### API_04 – Verify GET /users?page=-1 handles invalid page
**Start Time:** 26-06-2025 10:27  
**Steps:**
1. Open Postman.  
2. Send GET request to `/users?page=-1`.  
3. Observe response status and body.  
4. Validate error or empty data.  
**Result:** FAIL  
**Actual:** Returned status 200 with data instead of error.  
**Screenshot:** `ExecutionResults/Screenshots/API_04_fail.png`  
**End Time:** 26-06-2025 10:36

---

### API_05 – Verify GET /users?page=1 returns correct `per_page` count
**Start Time:** 26-06-2025 10:40  
**Steps:**
1. Open Postman.  
2. Send GET `/users?page=1`.  
3. Read `per_page` value.  
4. Count elements in `data[]`.  
**Result:** PASS  
**End Time:** 26-06-2025 10:47

---

### API_06 – Verify GET /users?page=abc returns error or empty
**Start Time:** 26-06-2025 10:50  
**Steps:**
1. Open Postman.  
2. Send GET `/users?page=abc`.  
3. Check status and `data[]`.  
4. Validate error or empty response.  
**Result:** FAIL  
**Actual:** Returned non-empty data instead of empty or error.  
**Screenshot:** `ExecutionResults/Screenshots/API_06_fail.png`  
**End Time:** 26-06-2025 10:58

---

### API_07 – Verify GET /users?page=1 pagination metadata present
**Start Time:** 26-06-2025 11:00
**Steps:**
1. Open Postman.  
2. Send GET `/users?page=1`.  
3. Verify `page`, `per_page`, `total`, `total_pages` fields.  
4. Confirm values plausible.  
**Result:** PASS  
**End Time:** 26-06-2025 11:06

---

### API_08 – Verify GET /users?page=1 supports CORS headers
**Start Time:** 26-06-2025 11:09  
**Steps:**
1. Open Postman.  
2. Send GET `/users?page=1`.  
3. Inspect response headers for CORS.  
4. Confirm `Access-Control-Allow-Origin: *`.  
**Result:** PASS  
**End Time:** 26-06-2025 11:16

---

## Single User Test Execution

**Client:** Postman v10.18.1  
**Environment:** Ubuntu 22.04 LTS  

---

### API_09 – Verify GET /users/1 returns 200 and correct user
**Start Time:** 26-06-2025 11:25  
**Steps:**
1. Open Postman.  
2. Send GET `/users/1`.  
3. Validate JSON schema for single user.  
4. Confirm `data.id = 1`.  
**Result:** PASS  
**End Time:** 26-06-2025 11:31

---

### API_10 – Verify GET /users/23 returns 404
**Start Time:** 26-06-2025 11:33  
**Steps:**
1. Open Postman.  
2. Send GET `/users/23`.  
3. Check response status.  
4. Confirm body is empty or `{}`.  
**Result:** FAIL  
**Actual:** Returned status 200 with empty data instead of 404.  
**Screenshot:** `ExecutionResults/Screenshots/API_10_fail.png`  
**End Time:** 26-06-2025 11:41

---

### API_11 – Verify GET /users/abc returns 404 or error
**Start Time:** 26-06-2025 11:43  
**Steps:**
1. Open Postman.  
2. Send GET `/users/abc`.  
3. Inspect status and body.  
4. Confirm error or empty.  
**Result:** PASS  
**End Time:** 26-06-2025 11:49

---

### API_12 – Verify GET /users/0 returns 404
**Start Time:** 26-06-2025 11:51  
**Steps:**
1. Open Postman.  
2. Send GET `/users/0`.  
3. Check response status.  
4. Confirm body empty.  
**Result:** FAIL  
**Actual:** Returned status 200 with default user data instead of 404.  
**Screenshot:** `ExecutionResults/Screenshots/API_12_fail.png`  
**End Time:** 26-06-2025 12:00

---

### API_13 – Verify GET /users/1 returns expected structure
**Start Time:** 26-06-2025 12:02  
**Steps:**
1. Open Postman.  
2. Send GET `/users/1`.  
3. Confirm `data.email` contains `@`.  
4. Confirm `support.url` present.  
**Result:** PASS  
**End Time:** 26-06-2025 12:08

---

### API_14 – Verify GET /users/2 repeated calls return consistent data
**Start Time:** 26-06-2025 12:10  
**Steps:**
1. Open Postman.  
2. Send GET `/users/2` twice.  
3. Compare both responses.  
4. Confirm identical data.  
**Result:** PASS  
**End Time:** 26-06-2025 12:17