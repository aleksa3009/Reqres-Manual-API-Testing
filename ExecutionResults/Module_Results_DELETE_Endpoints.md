# ExecutionResults/Module_Results_DELETE_Endpoints.md

**Client:** Postman v10.18.1  
**Environment:** Ubuntu 22.04 LTS  

---

## DELETE /users/{id} (3 cases)

### API_35 – Verify DELETE /users/2 returns 204 No Content  
**Start Time:** 28-06-2025 10:10  
**Steps:**  
- DELETE `https://reqres.in/api/users/2`  
- Click **Send**.  
**Result:** PASS  
**End Time:** 28-06-2025 10:15  

---

### API_36 – Verify DELETE /users/2 again returns 404  
**Start Time:** 28-06-2025 10:17  
**Steps:**  
- DELETE `https://reqres.in/api/users/2`  
- Click **Send**.  
**Result:** FAIL  
**Actual:** Returned `204 No Content` again instead of `404 Not Found`  
**Screenshot:** `ExecutionResults/Screenshots/API_36_fail.png`  
**End Time:** 28-06-2025 10:25  

---

### API_37 – Verify DELETE /users/abc returns error  
**Start Time:** 28-06-2025 10:27  
**Steps:**  
- DELETE `https://reqres.in/api/users/abc`  
- Click **Send**.  
**Result:** PASS  
**End Time:** 28-06-2025 10:32  

---