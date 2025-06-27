# ExecutionResults/Module_Results_POST_Endpoints.md

## POST Endpoint Test Execution (Postman)

**Client:** Postman v10.18.1  
**Environment:** Ubuntu 22.04 LTS 

---

## POST /register Endpoint Test Execution

---

### API_15 – Verify POST /register with valid data returns 200 and token  
**Start Time:** 27-06-2025 10:00  
**Steps:**  
- Open Postman.  
- Set method to `POST` and URL to `https://reqres.in/api/register`.  
- In the "Body" tab, select **raw**, set type to **JSON**, and enter payload:  
  `{"email":"eve.holt@reqres.in","password":"pistol"}`  
- Click **Send**.  
- Validate response status is `200`.  
- Confirm response body contains `id` (integer) and `token` (string).  
**Result:** PASS  
**End Time:** 27-06-2025 10:07  

---

### API_16 – Verify POST /register without password returns 400 and error  
**Start Time:** 27-06-2025 10:08  
**Steps:**  
- Open Postman.  
- Set method to `POST` and URL to `https://reqres.in/api/register`.  
- Body: `{"email":"sydney@fife"}`  
- Click **Send**.  
- Check that status is `400`.  
- Confirm response is `{ "error": "Missing password" }`.  
**Result:** FAIL  
**Actual:** Error is missing due to missing API key.  
**Screenshot:** `ExecutionResults/Screenshots/API_16_fail.png`  
**End Time:** 27-06-2025 10:14  

---

### API_17 – Verify POST /register without email returns 400  
**Start Time:** 27-06-2025 10:15  
**Steps:**  
- Open Postman.  
- Set method to `POST`, enter URL.  
- Payload: `{"password":"1234"}`  
- Click **Send**.  
- Expect status `400`, and error `Missing email or username`.  
**Result:** PASS  
**End Time:** 27-06-2025 10:21  

---

### API_18 – Verify POST /register with extra fields ignores extras  
**Start Time:** 27-06-2025 10:23  
**Steps:**  
- Open Postman.  
- POST with: `{"email":"eve.holt@reqres.in","password":"pistol","extra":"x"}`  
- Click **Send**.  
- Status should be `200`.  
- Response includes `id` and `token`; ignores extra.  
**Result:** PASS  
**End Time:** 27-06-2025 10:29  

---

### API_19 – Verify POST /register with blank password returns 400  
**Start Time:** 27-06-2025 10:31  
**Steps:**  
- Open Postman.  
- POST `{"email":"eve.holt@reqres.in","password":""}`  
- Send request.  
- Expect `400` with error `Missing password`.  
**Result:** FAIL  
**Actual:** Request succeeds unexpectedly.  
**Screenshot:** `ExecutionResults/Screenshots/API_19_fail.png`  
**End Time:** 27-06-2025 10:37  

---

### API_20 – Verify POST /register with invalid email format returns 400  
**Start Time:** 27-06-2025 10:38  
**Steps:**  
- POST with payload: `{"email":"not-an-email","password":"pistol"}`  
- Click Send.  
- Validate status 400 and error related to email.  
**Result:** PASS  
**End Time:** 27-06-2025 10:44  

---

### API_21 – Verify POST /register large payload handled  
**Start Time:** 27-06-2025 10:46  
**Steps:**  
- Construct large payload: same valid email/password repeated many times.  
- Send POST.  
- Confirm only one `token` returned.  
**Result:** PASS  
**End Time:** 27-06-2025 10:53  

---

### API_22 – Verify POST /register performance under 3s  
**Start Time:** 27-06-2025 10:55  
**Steps:**  
- Send valid register request.  
- Measure response time (Postman shows duration).  
- Should be < 3000ms.  
**Result:** PASS  
**End Time:** 27-06-2025 11:00  

---

## POST /login Endpoint Test Execution

---

### API_23 – Verify POST /login with valid credentials returns 200 and token  
**Start Time:** 27-06-2025 11:02  
**Steps:**  
- POST to `/login` with: `{"email":"eve.holt@reqres.in","password":"cityslicka"}`  
- Validate status 200 and token present.  
**Result:** PASS  
**End Time:** 27-06-2025 11:06  

---

### API_24 – Verify POST /login without password returns 400  
**Start Time:** 27-06-2025 11:08  
**Steps:**  
- POST: `{"email":"eve.holt@reqres.in"}`  
- Expect 400, with `Missing password` error.  
**Result:** FAIL  
**Actual:** No error shown.  
**Screenshot:** `ExecutionResults/Screenshots/API_24_fail.png`  
**End Time:** 27-06-2025 11:14  

---

### API_25 – Verify POST /login without email returns 400  
**Start Time:** 27-06-2025 11:16  
**Steps:**  
- POST with only `password`.  
- Status should be `400`.  
**Result:** PASS  
**End Time:** 27-06-2025 11:21  

---

### API_26 – Verify POST /login wrong password returns 400  
**Start Time:** 27-06-2025 11:23  
**Steps:**  
- POST with `eve.holt@reqres.in` and wrong password.  
- Expect status `400` with `user not found`.  
**Result:** PASS  
**End Time:** 27-06-2025 11:29  

---

### API_27 – Verify POST /login invalid email format returns 400  
**Start Time:** 27-06-2025 11:31  
**Steps:**  
- Email: `"bademail"` + valid password.  
- Should return `400`.  
**Result:** PASS  
**End Time:** 27-06-2025 11:38  

---

### API_28 – Verify POST /login performance under 3s  
**Start Time:** 27-06-2025 11:40  
**Steps:**  
- POST valid login.  
- Measure duration.  
- Ensure < 3000ms.  
**Result:** PASS  
**End Time:** 27-06-2025 11:47  

---