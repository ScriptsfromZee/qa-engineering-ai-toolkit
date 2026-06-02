# **Prompt 1: Test Case Generator**

**ROLE:** You are a Senior QA Engineer with 8+ years of experience in [WEB / MOBILE / API] testing, specialising in fintech/SaaS applications.

**CONTEXT:** You are writing test cases for the following requirement:

[PASTE REQUIREMENT HERE]

**TASK:** Generate [NUMBER] test cases. If no number is specified, generate the minimum complete set needed to achieve full coverage.

**FOR EACH TEST CASE, OUTPUT THIS EXACT STRUCTURE:**

- Test Case ID: TC-00X
- Title: [Action + condition, e.g. "Wallet funding fails below minimum"]
- Requirement Ref: [Quote the specific clause this case covers]
- Preconditions: [System state before test begins]
- Test Data: [Specific values, credentials, or inputs needed]
- Steps: [Numbered, atomic, one action per step]
- Expected Result: [Specific, measurable outcome]
- Test Type: [Functional / Negative / Edge Case / UI / Security]
- Priority: [Critical / High / Medium / Low] [Add this if it is used or needed for your product]
- Automation Candidate: [Yes / No, with one-line reason]

**COVERAGE RULES:** You must include at least:
happy path case, negative/validation cases, edge case (boundary value or unexpected input), security or access control case (if applicable)

**OUTPUT FORMAT:** Generate the test cases in [FORMAT].

Supported values:
- CSV
- Excel Table

If FORMAT = CSV:
- Output valid CSV only.
- Include headers in the first row.
- One test case per row.
- Escape commas using double quotes.
- Do not use markdown.

If FORMAT = Excel Table:
- Output as a markdown table suitable for direct paste into Excel.
- Use the following columns:
  Test Case ID | Title | Requirement Ref | Preconditions | Test Data | Steps | Expected Result | Test Type | Priority | Automation Candidate
- One test case per row.

Do not output any explanations outside the requested format. // This depends on what you want.

**CONFIDENCE SIGNAL:**
Rate your confidence in this output: [High / Medium / Low]
State in one sentence what information, if provided, would most improve this output.

**OPTIONAL MODIFIERS** (add any to the end of your prompt to make it more specific to you/your product):

- "Focus only on negative cases"
- "Assume automated execution — write steps for Selenium/Cypress"
- "Map cases to user story IDs: [LIST IDs]"
