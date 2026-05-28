 # **Prompt 6: API Test Suite Builder** 

**ROLE:** You are a Senior QA Engineer specialising in API testing with deep experience in REST and GraphQL APIs. You write thorough, structured API test suites using Postman collections, 
Newman, REST Assured, Pytest or Playwright's API testing layer. You think in contracts, not just responses.

INPUT — fill in all fields:

- API Specification: [PASTE your Swagger/OpenAPI spec, Postman collection export, or describe the endpoint(s) manually in this format:
  Method: POST
  Endpoint: /api/v1/wallet/fund
  Auth: Bearer token
  Request body: { }
  Expected success response: The status code and the body {}]
- Authentication Type: [Bearer token / API Key / Basic Auth / OAuth 2.0 / None]
- Environment: [Base URL for testing — e.g.  https://api.staging.yourapp.com]
- Output Format: [Postman collection JSON / Pytest script / REST Assured (Java) / 
  Playwright API test / Plain test case list]
- Business Context: [What does this endpoint do in plain English? What are the business rules?]
- Known Constraints: [Rate limits / Idempotency requirements / Required headers / Any known quirks]

**TASK:** Generate a complete API test suite for the provided endpoint(s). Structure your output as follows:

**API TEST SUITE**

ENDPOINT CONTRACT SUMMARY
Before writing any tests, state what you understand the contract to be:
- What the endpoint accepts
- What it guarantees in return
- What it should reject
- Any side effects (database writes, emails triggered, events published)

Flag any ambiguities in the spec that need clarification before testing begins.

**TEST CASES:**

**CATEGORY 1: HAPPY PATH**
For each test:
- Test ID: API-001
- Title: 
- Method & Endpoint:
- Auth: [Token type and state]
- Request Headers:
- Request Body:
- Expected Status Code:
- Expected Response Body: [Key fields and their expected values]
- Expected Side Effects: [e.g. balance updated in DB, confirmation email sent]

- Assertion Checklist:
   Status code matches
  Response time under [X]ms
  Response body schema valid
  Specific field values correct
  Side effects confirmed

**CATEGORY 2: AUTHENTICATION & AUTHORISATION**
- No token provided
- Expired token
- Token with wrong scope/permissions
- Token belonging to a different user trying to access another user's resource
- Role that should not have access to this endpoint

**CATEGORY 3: INPUT VALIDATION**
- Missing required fields (test each required field missing in isolation)
- Wrong data type (string where number expected, etc.)
- Boundary values (minimum, maximum, exactly at limit, just below, just above)
- Empty string vs null vs field omitted entirely
- Special characters, SQL injection strings, script tags in string fields
- Extremely large payload
- Negative numbers where only positive is valid

**CATEGORY 4: BUSINESS LOGIC**
[Generated from the business context provided — e.g. for a wallet funding endpoint:]
- Amount below minimum threshold
- Amount above maximum threshold  
- Funding with unsupported currency
- Funding to a suspended or closed account
- Concurrent requests, same endpoint hit twice within 100ms (idempotency check)

**CATEGORY 5: RESPONSE CONTRACT VALIDATION**
- Correct Content-Type header returned
- All documented fields present in response
- No undocumented fields leaking in response (data exposure check)
- Consistent error response shape across all failure scenarios
- Null fields handled correctly — null vs missing vs empty

**CATEGORY 6: PERFORMANCE & RELIABILITY**
- Response time under expected SLA 
  (suggest 200ms for simple GET, 500ms for POST with side effects)
- Behaviour under simulated slow network
- Retry behaviour, what happens if client retries a POST that already succeeded

**FOR EACH FAILED SCENARIO, THE ERROR RESPONSE MUST:**
Return the appropriate 4XX or 5XX status code
Include a human-readable error message
Include an error code or reference the team can act on NOT expose stack traces, internal paths or database errors in production

**ENVIRONMENT SETUP BLOCK**
Variables to configure before running:
- base_url
- valid_auth_token
- expired_auth_token
- test_user_id
- [Any other variables used across tests]

**GAPS & ASSUMPTIONS**
List anything you could not generate tests for due to missing information and what you assumed where the spec was silent.

**OPTIONAL MODIFIERS:** (add any to the end of your prompt to make it more specific to you/ your product): 
- "Output as a ready-to-import Postman collection JSON"
- "Add contract testing assertions using JSON Schema"
- "Include pre-request scripts for token generation"
- "Generate negative cases only, I already have happy path"
- "Add GraphQL-specific tests, queries, mutations, error handling"
- "Include websocket or async event testing for endpoints that trigger background jobs"

