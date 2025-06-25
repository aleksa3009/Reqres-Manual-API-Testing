## PUT /users/{id} (3 cases)

### API_29  
**Title:** Verify PUT /users/2 full update returns 200 and updated data  
**Preconditions:** Resource with id=2 exists  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. PUT `/users/2` with `{"name":"neo","job":"the one"}`.  
3. Status `200`.  
4. Body reflects `name` and `job` updated, contains `updatedAt`.  
**Priority:** High  
**Type:** Functional

### API_30  
**Title:** Verify PUT /users/999 returns 404 or handles gracefully  
**Preconditions:** Resource 999 does not exist  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. PUT `/users/999` with valid payload.  
3. Status `404` or `200` with created resource.  
4. Verify behavior documented.  
**Priority:** Medium  
**Type:** Negative

### API_31  
**Title:** Verify PUT /users/2 with empty body returns 400  
**Preconditions:** Resource 2 exists  
**Test Steps & Expected Results:**  
1. Open Postman → launched.  
2. PUT `/users/2` with `{}`.  
3. Status `400`.  
4. Error message present.  
**Priority:** Medium  
**Type:** Negative

---