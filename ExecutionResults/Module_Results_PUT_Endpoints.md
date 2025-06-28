# ExecutionResults/Module_Results_PUT_Endpoints.md

**Client:** Postman v10.18.1  
**Environment:** Ubuntu 22.04 LTS  

---

## PUT /users/{id} (3 cases)

### API_29 – Verify PUT /users/2 full update returns 200 and updated data  
**Start Time:** 28-06-2025 09:10  
**Steps:**  
- Open Postman.  
- Method: `PUT` URL: `https://reqres.in/api/users/2`  
- Body (raw JSON): `{ "name": "neo", "job": "the one" }`  
- Click **Send**.  
**Result:** PASS  
**End Time:** 28-06-2025 09:18  

---

### API_30 – Verify PUT /users/999 returns 404 or handles gracefully  
**Start Time:** 28-06-2025 09:20  
**Steps:**  
- Method: `PUT` URL: `https://reqres.in/api/users/999`  
- Body: valid JSON payload  
- Click **Send**.  
**Result:** FAIL  
**Actual:** Returned `200 OK` creating new resource instead of `404 Not Found`  
**Screenshot:** `ExecutionResults/Screenshots/API_30_fail.png`  
**End Time:** 28-06-2025 09:28  

---

### API_31 – Verify PUT /users/2 with empty body returns 400  
**Start Time:** 28-06-2025 09:30  
**Steps:**  
- Method: `PUT` URL: `https://reqres.in/api/users/2`  
- Body: `{}`  
- Click **Send**.  
**Result:** FAIL  
**Actual:** Returned `200 OK` with no validation error  
**Screenshot:** `ExecutionResults/Screenshots/API_31_fail.png`  
**End Time:** 28-06-2025 09:38  

---
