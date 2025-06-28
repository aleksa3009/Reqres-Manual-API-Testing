# Bug Retest Results – 28-06-2025

## Retest Execution Summary
Re-tested all previously logged bugs in Postman (v11.49.3).

---

### Bug ID: #1 - API_02: [BUG] Unexpected API key requirement on public GET endpoint
- **Retested in Postman v11.49.3**  
- **Status:** Still Reproducible  
- **Comment:** Error message "Missing API key" persists.

---

### Bug ID: #2 – API_04: [BUG] GET /users?page=-1 returns data instead of error or empty
- **Retested in Postman v11.49.3**  
- **Status:** Fixed  
- **Comment:** Response status shows `200 OK` with empty `data[]`.

---

### Bug ID: #3 – API_06: [BUG] GET /users?page=abc returns data instead of error or empty
- **Retested in Postman v11.49.3**  
- **Status:** Not Reproducible  
- **Comment:** Shows `401 Unauthorized` error.

---

### Bug ID: #4 – API_10: [BUG] GET /users/23 returns 200 instead of 404(Chrome)
- **Retested in Postman v11.49.3**  
- **Status:** Still Reproducible  
- **Comment:** Showing same error, needs fix.

---

### Bug ID: #5 – API_12: [BUG] GET /users/0 returns default user data instead of 404
- **Retested in Postman v11.49.3**  
- **Status:** Fixed  
- **Comment:** Response status `404 Not Found` and empty response.

---

### Bug ID: #6 – API_16: [BUG] POST /register without password returns wrong error
- **Retested in Postman v11.49.3**  
- **Status:** Still Reproducible  
- **Comment:** No feedback on "Missing API Keys", remains unsolved.

---

### Bug ID: #7 – API_19: [BUG] POST /register with blank password succeeds unexpectedly
- **Retested in Postman v11.49.3**  
- **Status:** Fixed  
- **Comment:** Response status shows `400 Bad Request` with email and password in `JSON body`.

---

### Bug ID: #8 – API_24: [BUG] POST /login without password shows no error
- **Retested in Postman v11.49.3**  
- **Status:** Not Reproducible  
- **Comment:** Response Status `403 Forbidden Error` , needs fix

---
 

