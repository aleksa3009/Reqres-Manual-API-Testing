# Test Data for Reqres.in API Manual Testing

This folder contains JSON files with test data used for manual testing of the Reqres.in REST API.

## Files

- `valid_payloads.json`  
  Contains valid JSON payloads for successful requests, such as user registration, login, and data updates.

- `invalid_payloads.json`  
  Contains various invalid JSON payloads intended for negative testing scenarios.  
  Examples include:  
  - Missing required fields  
  - Incorrect data formats (e.g., email without '@')  
  - Empty strings or wrong data types  
  - Overly long strings or special characters  

## Usage Recommendations

- Use the valid payloads to test positive scenarios.  
- Use the invalid payloads to verify how the API handles errors and invalid inputs.  
- Add new test data as needed, following the existing structure.

