# ExecutionResults/Module_Results_PATCH_Endpoints.md

**Client:** Postman v10.18.1  
**Environment:** Ubuntu 22.04 LTS  

---

## GET /unknown/{id} (3 cases)

### API_38 – Verify GET /unknown returns metadata list 200  
**Start Time:** 28-06-2025 10:40  
**Steps:**  
- GET `https://reqres.in/api/unknown`  
- Click **Send**.  
**Result:** PASS  
**End Time:** 28-06-2025 10:45  

---

### API_39 – Verify GET /unknown/3 returns 200 and correct resource  
**Start Time:** 28-06-2025 10:47  
**Steps:**  
- GET `https://reqres.in/api/unknown/3`  
- Click **Send**.  
**Result:** PASS  
**End Time:** 28-06-2025 10:53  

---

### API_40 – Verify GET /unknown/23 returns 404  
**Start Time:** 28-06-2025 10:55  
**Steps:**  
- GET `https://reqres.in/api/unknown/23`  
- Click **Send**.  
**Result:** PASS  
**End Time:** 28-06-2025 11:00  

---