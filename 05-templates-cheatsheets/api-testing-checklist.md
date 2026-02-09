# API Testing Checklist

> **Complete checklist for thorough API testing**

---

## 📋 Pre-Testing Setup

- [ ] API documentation reviewed
- [ ] Base URL confirmed (Dev/QA/UAT)
- [ ] Authentication tokens/keys obtained
- [ ] Postman collection created
- [ ] Test data prepared

---

## 🔍 Functional Testing

### Request Validation

- [ ] **Valid request succeeds**
  - Correct HTTP method (GET/POST/PUT/DELETE)
  - Valid endpoint URL
  - Required headers included
  - Valid request body/payload

- [ ] **Invalid request fails appropriately**
  - Wrong HTTP method
  - Invalid endpoint
  - Missing required headers
  - Malformed JSON/XML
  - Missing required fields

### Response Validation

- [ ] **Status Code is correct**
  - 200 OK (successful GET/PUT/PATCH)
  - 201 Created (successful POST)
  - 204 No Content (successful DELETE)
  - 400 Bad Request (invalid input)
  - 401 Unauthorized (missing/invalid auth)
  - 403 Forbidden (insufficient permissions)
  - 404 Not Found (resource doesn't exist)
  - 500 Internal Server Error (server issue)

- [ ] **Response body is valid**
  - JSON/XML structure is correct
  - All expected fields present
  - Data types are correct (string, number, boolean)
  - Values are within expected range

- [ ] **Response time is acceptable**
  - Response < 2 seconds (normal)
  - Response < 5 seconds (acceptable)

---

## 🎯 HTTP Methods Testing

### GET Requests

- [ ] Retrieve single resource by ID
- [ ] Retrieve list of resources
- [ ] Filter with query parameters
- [ ] Pagination works correctly
- [ ] Sorting works correctly
- [ ] Invalid ID returns 404
- [ ] Empty results return empty array (not error)

### POST Requests

- [ ] Create new resource with valid data
- [ ] Response includes created resource
- [ ] Response includes resource ID/location
- [ ] Duplicate creation handled (409 Conflict or success)
- [ ] Missing required fields returns 400
- [ ] Invalid data type returns 400
- [ ] Created resource persists (verify with GET)

### PUT Requests

- [ ] Update existing resource completely
- [ ] Response shows updated values
- [ ] Non-existent ID returns 404
- [ ] Invalid data returns 400
- [ ] Updated resource persists (verify with GET)

### PATCH Requests

- [ ] Partial update works
- [ ] Only specified fields updated
- [ ] Other fields remain unchanged
- [ ] Invalid field name handled

### DELETE Requests

- [ ] Delete existing resource succeeds
- [ ] Response confirms deletion (204 or 200)
- [ ] Deleted resource no longer accessible (GET returns 404)
- [ ] Delete non-existent resource returns 404
- [ ] Delete already deleted resource handled

---

## 🔐 Authentication & Authorization

- [ ] **No authentication**
  - Unauthenticated request returns 401

- [ ] **Invalid authentication**
  - Wrong token/key returns 401
  - Expired token returns 401
  - Malformed token returns 401

- [ ] **Valid authentication**
  - Correct token allows access
  - Token included in correct header

- [ ] **Authorization levels**
  - Admin can access admin endpoints
  - Regular user cannot access admin endpoints (403)
  - User can only access own data
  - User cannot access other users' data (403)

---

## 📊 Data Validation

### Input Validation

- [ ] **String fields**
  - Minimum length enforced
  - Maximum length enforced
  - Special characters handled
  - Empty string handled
  - Null value handled

- [ ] **Numeric fields**
  - Minimum value enforced
  - Maximum value enforced
  - Decimal/integer type correct
  - Negative numbers handled
  - Zero handled
  - Non-numeric input rejected

- [ ] **Date fields**
  - Valid date format accepted
  - Invalid date format rejected
  - Future dates handled
  - Past dates handled

- [ ] **Email fields**
  - Valid email accepted
  - Invalid email rejected

- [ ] **Enum/Select fields**
  - Valid options accepted
  - Invalid options rejected

### Boundary Testing

- [ ] Minimum value
- [ ] Minimum + 1
- [ ] Maximum - 1
- [ ] Maximum value
- [ ] Below minimum (should fail)
- [ ] Above maximum (should fail)

---

## 🧪 Error Handling

- [ ] **Error response structure**
  - Contains error message
  - Contains error code
  - Message is descriptive
  - No sensitive data exposed (stack traces, DB errors)

- [ ] **Common errors tested**
  - 400: Invalid input format
  - 401: Missing authentication
  - 403: Insufficient permissions
  - 404: Resource not found
  - 409: Conflict (duplicate)
  - 422: Validation error
  - 500: Server error

---

## 🔄 State & Workflow Testing

- [ ] **Create → Read → Update → Delete flow**
  1. POST: Create resource
  2. GET: Verify created
  3. PUT/PATCH: Update resource
  4. GET: Verify updated
  5. DELETE: Remove resource
  6. GET: Verify deleted (404)

- [ ] **State transitions**
  - Order: pending → processing → shipped → delivered
  - Payment: pending → completed → refunded
  - Invalid state transitions rejected

---

## 📝 Headers Testing

### Request Headers

- [ ] Content-Type: application/json (when sending JSON)
- [ ] Accept: application/json (when expecting JSON)
- [ ] Authorization: Bearer <token>
- [ ] Custom headers required by API

### Response Headers

- [ ] Content-Type matches response format
- [ ] Cache-Control present (if applicable)
- [ ] CORS headers present (if applicable)
- [ ] Rate limit headers (if applicable)

---

## 🔢 Special Cases

### Large Data

- [ ] Large payload (>1MB) handled
- [ ] Large array (1000+ items) handled
- [ ] Long string (10,000+ characters) handled

### Special Characters

- [ ] Unicode characters
- [ ] Emojis
- [ ] HTML tags (should be escaped)
- [ ] SQL injection attempts (should be rejected)
- [ ] Script injection attempts (should be rejected)

### Edge Cases

- [ ] Empty array []
- [ ] Empty object {}
- [ ] Null values
- [ ] Missing optional fields
- [ ] Extra unexpected fields

---

## 🔗 Integration Testing

- [ ] **Database verification**
  - Created data exists in DB
  - Updated data reflects in DB
  - Deleted data removed from DB
  - Data format matches DB schema

- [ ] **Related endpoints**
  - Creating A affects endpoint B
  - Deleting A affects endpoint B
  - Dependencies handled correctly

---

## ⚡ Performance Testing

- [ ] Single request response time < 2s
- [ ] Concurrent requests handled (10+ users)
- [ ] Large dataset pagination works
- [ ] Rate limiting enforced (if applicable)

---

## 📄 Documentation Testing

- [ ] API docs match actual behavior
- [ ] All endpoints documented
- [ ] Request examples accurate
- [ ] Response examples accurate
- [ ] Error codes documented

---

## ✅ Quick Test Template

```
Endpoint: POST /api/users
Purpose: Create new user

Test Cases:
✓ Valid user creation
  - Request: { name: "John", email: "john@test.com" }
  - Expected: 201, user object returned

✓ Missing required field
  - Request: { name: "John" }  # email missing
  - Expected: 400, error message

✓ Invalid email format
  - Request: { name: "John", email: "invalid" }
  - Expected: 400, error message

✓ Duplicate email
  - Request: { name: "Jane", email: "john@test.com" }  # already exists
  - Expected: 409 or 400, error message

✓ Database verification
  - Query: SELECT * FROM users WHERE email = 'john@test.com'
  - Expected: User exists with correct data
```

---

## 🎯 Priority Levels

### P0 - Critical (Must Test)
- Happy path (valid request)
- Authentication
- Database persistence
- Error handling for invalid input

### P1 - High (Should Test)
- All CRUD operations
- Boundary values
- Common error scenarios

### P2 - Medium (Nice to Test)
- Edge cases
- Special characters
- Performance

### P3 - Low (Optional)
- Rarely used features
- Extreme edge cases

---

**Remember:** Start with P0 tests, then work your way down based on time available! 🚀
