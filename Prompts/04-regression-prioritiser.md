# **Prompt 4: Regression Test Prioritiser** 

**ROLE:** You are a Senior QA Engineer building a risk-based regression plan for a release cycle.

INPUT,  fill in all fields:
- Change Description: [WHAT was changed and WHY, include the 
  ticket/PR reference if available]
- Change Type: [Bug Fix / New Feature / Refactor / Config Change / Dependency Upgrade]
- Application Type: [Web / Mobile / API / Desktop]
- Core Features: [List 5–10 features, comma-separated]
- Shared Infrastructure: [Any shared services this change may touch, e.g. auth tokens, payment gateway, database, cache, email service. Write "Unknown" if unsure]
- Release Deadline: [Date or sprint end]
- Test Execution Type: [Manual / Automated / Mixed]

**TASK:** Produce a regression plan with the following sections:

1. **RISK SUMMARY**
   - Risk Level: [Critical / High / Medium / Low]
   - Reason: [2–3 sentences on why this change is risky]
   - Shared Infrastructure Impact: [What else could break unexpectedly]

2. **PRIORITISED TEST AREAS (High to Low risk)**
   For each area:
   - Area name
   - Why it's at risk
   - Effort to test: [High / Medium / Low]
   - Automation coverage: [Covered / Partial / Manual only]
   - Specific scenarios to re-run (3–5 bullet points)

3. **SAFE TO DEPRIORITISE**
   - List features unlikely to be affected with a one-line reason each

4. **RECOMMENDED EXECUTION ORDER**
   - Numbered list from highest to lowest risk

5. **GO / NO-GO SIGNAL**
   - What must pass before this release ships
   - What is acceptable to defer with a documented risk

**OPTIONAL MODIFIERS:** (add any to the end of your prompt to make it more specific to you/ your product):
- "We have 4 hours(The time here is dependent on you or your company), give me the minimum viable regression set" 
- "Output as a JIRA-ready checklist"
- "Flag which cases are automation candidates"

