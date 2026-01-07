# Use Case Validation Guide

> **Purpose**: Ensure use cases meet quality standards before they're used for development.

---

## When to Validate

Validate use cases:
- **Before referencing in roadmap tasks** — ensure the use case is ready for implementation
- **When creating a new use case** — catch issues early
- **Before starting implementation** — agents should validate the use case they're about to implement
- **When reviewing PRs** — if a use case is added or modified, validate it

---

## Validation Checklist

Use this checklist to verify a use case meets quality standards. A use case should pass all criteria before being used for development.

### 1. Completeness

- [ ] **Title** is present and action-oriented (e.g., "User Logs In", not "Login")
- [ ] **Primary Actor** is specified and specific (e.g., "Registered User", not just "User")
- [ ] **Goal** is clearly stated and describes what the actor wants to achieve
- [ ] **Preconditions** are listed (can be empty list if none required)
- [ ] **Main Success Scenario** has numbered steps (at least 3 steps)
- [ ] **Extensions** section is present (can be empty if no extensions needed)

### 2. Clarity

- [ ] Goal is **specific** — not vague or ambiguous
- [ ] Goal is **achievable** — something the system can actually do
- [ ] Goal is **valuable** — provides clear value to the actor
- [ ] Actor is **specific** — not generic (e.g., "Registered User" not "User")
- [ ] All steps in Main Success Scenario are clear and unambiguous

### 3. Testability

- [ ] Main Success Scenario provides clear acceptance criteria
- [ ] Each step is testable (can verify it happened)
- [ ] Extensions cover key error cases and alternatives
- [ ] Preconditions are testable (can verify they're met)

### 4. Implementation-Agnostic

- [ ] No UI elements mentioned (e.g., "click button", "form field")
- [ ] No API endpoints or technical details
- [ ] No database schema or data structure details
- [ ] No framework or library names
- [ ] Focuses on **what** happens, not **how** it's implemented

### 5. User Perspective

- [ ] Written from the actor's point of view
- [ ] Uses actor's language, not technical jargon
- [ ] Describes user goals, not system functions
- [ ] Steps alternate between actor actions and system responses

### 6. Consistency

- [ ] Follows file naming convention (kebab-case, descriptive)
- [ ] Follows template format from `TEMPLATE.md`
- [ ] Extensions reference step numbers correctly (e.g., "3a", "3a1")
- [ ] Consistent terminology with other use cases

### 7. Scope

- [ ] **One clear goal** per use case
- [ ] Goal is achievable in a single interaction/session
- [ ] Not trying to solve multiple problems
- [ ] If multiple goals, should be split into separate use cases

### 8. Completeness of Scenarios

- [ ] Main Success Scenario is complete (reaches a clear end state)
- [ ] Extensions cover important alternatives
- [ ] Extensions cover common error cases
- [ ] Each extension has a clear resolution or end point

---

## Common Issues to Watch For

### ❌ Too Technical

**Bad:**
```
1. User sends POST request to /api/login
2. System validates JWT token
3. System returns 200 status code
```

**Good:**
```
1. User provides credentials
2. System validates credentials
3. System confirms successful authentication
```

### ❌ Too Vague

**Bad:**
```
Goal: User logs in
```

**Good:**
```
Goal: User authenticates to access their account
```

### ❌ Multiple Goals

**Bad:**
```
Goal: User logs in and views their profile
```

**Good:**
Split into two use cases:
- "User Logs In"
- "User Views Profile"

### ❌ UI-Specific

**Bad:**
```
1. User clicks the login button
2. User fills in the email field
3. User submits the form
```

**Good:**
```
1. User provides email address
2. User provides password
3. User requests authentication
```

### ❌ Missing Extensions

**Bad:**
```
Main Success Scenario:
1. User provides credentials
2. System authenticates user

Extensions: (none)
```

**Good:**
```
Main Success Scenario:
1. User provides credentials
2. System authenticates user

Extensions:
2a. Invalid credentials provided:
    2a1. System rejects authentication
    2a2. System informs user of failure
    2a3. Use case ends
```

### ❌ Generic Actor

**Bad:**
```
Primary Actor: User
```

**Good:**
```
Primary Actor: Registered User
```

---

## Validation Prompt Template

Use this prompt template for AI-assisted validation:

```
Please validate the following use case against our quality standards.

Use Case File: [path to use case file]

Validation Criteria:
1. Completeness - All required elements present
2. Clarity - Goal is clear, specific, and unambiguous
3. Testability - Scenarios provide clear acceptance criteria
4. Implementation-agnostic - No technical details, UI elements, or API specifics
5. User perspective - Written from actor's point of view
6. Consistency - Follows naming conventions and format
7. Scope - One clear goal per use case
8. Completeness of scenarios - Main scenario complete, extensions cover key alternatives/errors

Please provide:
1. A pass/fail for each criterion
2. Specific issues found (if any)
3. Suggestions for improvement (if any)
4. Overall assessment: Ready for development / Needs revision
```

---

## Validation Workflow

### For Humans (Creating Use Cases)

1. Write the use case following the template
2. Review against the checklist above
3. Use the validation prompt with an AI assistant if needed
4. Fix any issues found
5. Mark as validated (add a note or checklist completion)
6. Reference in roadmap tasks

### For Agents (Before Implementation)

1. Read the use case referenced in the roadmap task
2. Validate against the checklist
3. If issues are found:
   - Report them to the human
   - Ask for clarification or revision
   - Do not proceed until use case is validated
4. If validated:
   - Proceed with implementation
   - Use the use case as the source of truth

---

## Examples

### ✅ Good Use Case

```markdown
# User Logs In

## Primary Actor
Registered User

## Goal
User authenticates to access their account

## Preconditions
- User has an account
- User is not currently logged in

## Main Success Scenario
1. User provides email address
2. User provides password
3. User requests authentication
4. System validates credentials
5. System confirms successful authentication
6. System grants access to user account

## Extensions
3a. Invalid email format:
    3a1. System rejects input
    3a2. System requests valid email
    3a3. Use case resumes at step 1

4a. Invalid credentials:
    4a1. System rejects authentication
    4a2. System informs user of failure
    4a3. Use case ends
```

**Why it's good:**
- Clear, specific goal
- Specific actor
- Complete scenario
- Covers key error cases
- Implementation-agnostic
- User perspective

### ❌ Problematic Use Case

```markdown
# Login

## Primary Actor
User

## Goal
Login

## Main Success Scenario
1. Click login button
2. Fill form
3. Submit
4. Get response
```

**Issues:**
- Title too vague
- Actor too generic
- Goal unclear
- UI-specific language
- Missing preconditions
- Missing extensions
- Steps too vague
- No clear end state

---

## Quick Reference

**Before using a use case for development, verify:**

- ✅ All required elements present
- ✅ Goal is clear and specific
- ✅ No technical/UI details
- ✅ Written from user perspective
- ✅ One clear goal
- ✅ Complete scenarios with error handling
- ✅ Follows naming and format conventions

**If any item fails, revise the use case before proceeding.**

---

## Related Documents

- [README.md](./README.md) - Use case guide
- [TEMPLATE.md](./TEMPLATE.md) - Use case template

