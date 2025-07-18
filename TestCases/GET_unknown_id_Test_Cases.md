## GET /unknown/{id} (3 cases)

### API_38  
**Title:** Verify GET /unknown returns metadata list 200  

**Preconditions:**  
- None  

**Test Steps:**  
1. Open Postman.  
2. Set method to GET and URL to `https://reqres.in/api/unknown`.  
3. Send the request.  

**Expected Results:**  
- HTTP status code `200 OK`.  
- Response body contains `data[]` array with resource metadata fields: `id`, `name`, `year`, `color`, `pantone_value`.  
- Response header `Content-Type` is `application/json`.  
- Response time is less than 3 seconds.  

**Priority:** High  

**Type:** Functional 

---

### API_39  
**Title:** Verify GET /unknown/3 returns 200 and correct resource

**Preconditions:**  
- Verify resource existence with GET /unknown/3 before test execution  

**Test Steps:**  
1. Open Postman.  
2. Set method to GET and URL to `https://reqres.in/api/unknown/3`.  
3. Send the request.  

**Expected Results:**  
- HTTP status code `200 OK`.  
- Response body contains `data.id` equal to `3`.  
- Response body includes correct `name`, `year`, `color`, and `pantone_value` fields.  
- Response header `Content-Type` is `application/json`.  
- Response time is less than 3 seconds.
-   
**Priority:** High  

**Type:** Functional 

---

### API_40  
**Title:** Verify GET /unknown/23 returns 404  

**Preconditions:**  
- Resource with id=23 does not exist 
   
**Test Steps:**  
1. Open Postman.  
2. Set method to GET and URL to `https://reqres.in/api/unknown/23`.  
3. Send the request.  
   
**Expected Results:**  
- HTTP status code `404 Not Found`.  
- Response body is empty or contains appropriate error message.  
- Response header `Content-Type` is `application/json`.  
- Response time is less than 3 seconds.  

**Priority:** Medium  

**Type:** Negative  

---