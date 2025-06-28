# ExecutionResults/Module_Results_PATCH_Endpoints.md

**Client:** Postman v10.18.1  
**Environment:** Ubuntu 22.04 LTS  

---

## PATCH /users/{id} (3 cases)

### API_32 – Verify PATCH /users/2 partial update of name returns 200  
**Start Time:** 28-06-2025 09:40  
**Steps:**  
- Method: `PATCH` URL: `https://reqres.in/api/users/2`  
- Body (raw JSON): `{ "name": "morpheus" }`  
- Click **Send**.  
**Result:** PASS  
**End Time:** 28-06-2025 09:48  

---

### API_33 – Verify PATCH /users/2 with empty payload returns 400  
**Start Time:** 28-06-2025 09:50  
**Steps:**  
- Method: `PATCH` URL: `https://reqres.in/api/users/2`  
- Body: `{}`  
- Click **Send**.  
**Result:** FAIL  
**Actual:** Returned `200 OK` instead of `400 Bad Request`  
**Screenshot:** `ExecutionResults/Screenshots/API_33_fail.png`  
**End Time:** 28-06-2025 09:58  

---

### API_34 – Verify PATCH /users/999 returns 404 or empty response  
**Start Time:** 28-06-2025 10:00  
**Steps:**  
- PATCH to `https://reqres.in/api/users/999` with valid payload  
- Click **Send**.  
**Result:** PASS  
**End Time:** 28-06-2025 10:05  

---
