---
name: salesforce-test-overwatch
description: Run all Salesforce Apex tests via the sf CLI, analyze failures, and create a fix plan for user review
user-invocable: true
---

When the user invokes this skill, follow these steps in order:

## Step 1 — Run All Apex Tests

Run the Salesforce CLI command to execute all tests with detailed output:

```
sf apex run test --test-level RunLocalTests --result-format json --wait 30 --code-coverage
```

- If the org is not authenticated or the command fails to connect, stop and tell the user.
- Wait for the full test run to complete before proceeding.

## Step 2 — Parse and Summarize Results

From the JSON output, extract:

1. **Total tests run**, **passed**, **failed**, and **skipped** counts
2. For each **failing test**:
   - Test class name and method name
   - The failure message and stack trace
   - The line number where the failure occurred
3. **Code coverage** summary (overall percentage and any classes below 75%)

Present a concise summary table to the user showing the test results overview before proceeding.

## Step 3 — Analyze Failures and Read Relevant Source

For each failing test:

1. Read the **test class** source file to understand what the test expects
2. Read the **class under test** (identified from the stack trace or test method body) to understand the production code
3. Identify the root cause of each failure (e.g., assertion mismatch, null pointer, missing test data, DML error, governor limit)

## Step 4 — Create a Fix Plan

Enter plan mode and create a structured plan that includes:

- **One section per failing test** with:
  - The test class and method name
  - Root cause analysis
  - Proposed fix (whether the test or the production code needs to change)
  - Specific file(s) and line(s) to modify
- **A section for code coverage gaps** (if any classes are below 75%) with recommendations

## Step 5 — Prompt for User Review

After presenting the plan, explicitly ask the user:

> Here is the proposed fix plan. Please review each item and let me know if you'd like to:
> 1. **Accept all** — I'll implement every fix
> 2. **Accept with changes** — tell me which items to modify or skip
> 3. **Reject** — discard the plan

**Do NOT begin implementing any fixes until the user has explicitly accepted the plan.**
