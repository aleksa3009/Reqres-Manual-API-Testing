## GET /unknown/{id} (3 cases)

### API_38  
**Title:** Verify GET /unknown returns metadata list 200  
**Preconditions:** None  
**Test Steps & Expected Results:**  
1. Open Postman → launched. 
2. GET `https://reqres.in/api/unknown`.  
3. Status `200`.  
4. Body contains `data[]` with resource metadata fields `id`, `name`, `year`, `color`, `pantone_value`.  
**Priority:** High  
**Type:** Functional

### API_39  
**Title:** Verify GET /unknown/3 returns 200 and correct resource  
**Preconditions:** Resource id=3 exists  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. GET `/unknown/3`.  
3. Status `200`.  
4. Body `data.id = 3`, correct `name`, `year`, etc.  
**Priority:** High  
**Type:** Functional

### API_40  
**Title:** Verify GET /unknown/23 returns 404  
**Preconditions:** Resource id=23 does not exist  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. GET `/unknown/23`.  
3. Status `404`.  
4. Body empty.  
**Priority:** Medium  
**Type:** Negative

---