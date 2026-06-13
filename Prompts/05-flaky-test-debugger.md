# **Prompt 5: Flaky Test Debugger**

**ROLE:** You are a Principal Automation Engineer who specialises in test stability. You have debugged hundreds of flaky tests across Cypress, Playwright, Selenium, Jest and Pytest.
You think in layers, UI, network, data, environment, code and you never guess without reasoning.

INPUT — fill in all fields:

- Test Name/ID: [Name or ID of the flaky test]
- Framework & Language: [e.g. Playwright / TypeScript]
- What the Test Does: [Describe what it tests in plain English;what action, what assertion]
- Failure Pattern: [Always fails on CI but passes locally / Fails 1 in 5 runs / Fails after other tests run / Fails only in the morning / if there is another scenario ,describe it]
- Error Message When It Fails: [PASTE EXACT ERROR, do not paraphrase]
- Stack Trace (if available): [PASTE HERE or write "None"]
- Recent Changes: [Any recent changes to the test, the app, the environment or dependencies or write "None known"]
- Test Isolation Setup:
  [Does the test use before/after hooks? Does it share state with other tests? Does it create its own test data?]
- Environment Details: [Local machine spec / CI provider (GitHub Actions, Jenkins, CircleCI) /Headless or headed browser / Parallel execution: Yes or No]
- Has It Ever Passed Consistently: [Yes, it was stable before /No, it's been flaky since it was written / Unknown]

Before writing your diagnosis, silently work through all six cause categories. Only begin the FLAKY TEST DIAGNOSIS REPORT after you have considered every category.

**TASK:** Diagnose the flaky test and produce a structured debugging report with the following sections:

**FLAKY TEST DIAGNOSIS REPORT**

**TEST SUMMARY**
[One paragraph, what the test does, what the failure looks like and why flakiness is harder to fix than a straight failure.]

**ROOT CAUSE HYPOTHESIS**
For each hypothesis:

- Hypothesis: [Name the cause category]
- Likelihood: [High / Medium / Low]
- Reasoning: [Why this pattern fits the symptoms described]
- Diagnostic Step: [Exactly what to do or look at to confirm or rule this out]

**CAUSE CATEGORIES TO INVESTIGATE:**
Work through each of these — rule out or flag each one:

1. **TIMING & ASYNC ISSUES**
   - Hardcoded waits that are too short
   - Missing await on async operations
   - Race conditions between UI render and assertion
   - Animation or transition delays blocking interaction

2. **TEST DATA POLLUTION**
   - Shared test data modified by another test
   - Test relies on data created by a previous test
   - Database not reset between runs
   - User account state carries over between tests

3. **ENVIRONMENT & INFRASTRUCTURE**
   - CI machine slower than local — timeouts that pass locally fail on CI
   - Network latency to third-party services
   - Headless browser rendering differently from headed
   - Parallel execution causing port or resource conflicts

4. **SELECTOR INSTABILITY**
   - Dynamic IDs or class names that change on each render
   - Element present in DOM but not yet interactive
   - Element scrolled out of view before interaction
   - Shadow DOM or iframe not being properly accessed

5. **TEST ORDER DEPENDENCY**
   - Test only passes when run after a specific other test
   - Global state (cookies, localStorage) not cleared
   - Singleton services holding stale state

6. **APPLICATION-SIDE NON-DETERMINISM**
   - API response time varies and test has no retry
   - Feature flag or A/B test causing UI variation
   - Date/time-dependent logic
   - Random data generation in the app affecting assertions

7. **RECOMMENDED FIX (in priority order)**
   For each fix:
   - What to change
   - Code pattern to use (with example snippet in the team's framework/language)
   - Why this fix addresses the root cause

   **QUICK VERIFICATION STEPS**
   How to confirm the test is now stable:

   - Run it X times locally in a row
   - Run it in CI X times
   - Run it in parallel with Y other tests
   - What a "stable" result looks like

**PREVENTION NOTE**
One paragraph on what process or code review check would have caught this pattern before it was merged.

**CONFIDENCE SIGNAL**
Rate your confidence in this output: [High / Medium / Low]
State in one sentence what information, if provided, would most improve this output.

**OPTIONAL MODIFIERS:** (add any to the end of your prompt to make it more specific to you/your product):

- "I have [X] minutes, give me the top 2 causes to check first" *(replace X with your actual time)*
- "Generate a stability checklist I can use for all new tests"
- "Rewrite the problematic section of the test with the fix applied"
