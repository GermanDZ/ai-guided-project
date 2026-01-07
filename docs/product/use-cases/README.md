# Use Cases

> **Document Type**: State (keep current)
> 
> This directory contains use case documentation following Alistair Cockburn's approach from "Writing Effective Use Cases."

---

## What Are Use Cases?

Use cases describe **what** the system should do from the user's perspective. They focus on user goals and interactions, not implementation details. Each use case documents one complete user goal—a story of how an actor (user, system, or external service) achieves a specific outcome.

### Why Use Cases?

- **Source of Truth**: Use cases define what features should do, independent of how they're implemented
- **User-Centered**: They describe behavior from the user's perspective, ensuring we build the right thing
- **Clear Scope**: Each use case has a clear goal and boundaries
- **Testable**: The scenarios provide clear acceptance criteria
- **Communication**: They serve as a common language between product, development, and stakeholders

---

## Use Case Format

We use a simplified version of Cockburn's format, focusing on the essential elements:

### Required Elements

1. **Title** - A clear, action-oriented name (e.g., "User Logs In")
2. **Primary Actor** - Who initiates the use case (e.g., "Registered User", "System Administrator")
3. **Goal** - What the actor wants to achieve
4. **Preconditions** - What must be true before the use case can start
5. **Main Success Scenario** - The happy path, step by step
6. **Extensions** - Alternative flows and error handling

### Optional Elements

- **Secondary Actors** - Other actors involved (if any)
- **Related Use Cases** - Links to other use cases (includes, extends, or generalizes)
- **Postconditions** - What must be true after successful completion
- **Business Rules** - Domain-specific constraints or rules

---

## How to Write a Use Case

### 1. Start with the Goal

Ask: "What does the actor want to achieve?" The goal should be:
- **Specific**: Clear and unambiguous
- **Achievable**: Something the system can actually do
- **Valuable**: Provides value to the actor

### 2. Identify the Actor

Who initiates this use case? Be specific:
- ✅ "Registered User" (not just "User")
- ✅ "System Administrator" (not just "Admin")
- ✅ "Payment Gateway" (for external systems)

### 3. Write the Main Success Scenario

This is the "happy path"—the most common, straightforward way the use case succeeds. Write it as numbered steps:

```
1. Actor does something
2. System responds
3. Actor does something else
4. System responds
...
```

**Guidelines:**
- Use simple, declarative sentences
- Focus on **what** happens, not **how** it's implemented
- Each step should be at the same level of detail
- Keep it concise—typically 3-10 steps

### 4. Add Extensions

Extensions handle alternatives and errors. Format them as:

```
3a. Invalid input provided:
    3a1. System displays error message
    3a2. System returns to step 2
```

Extensions can be:
- **Alternative flows**: Different ways to achieve the same goal
- **Error handling**: What happens when something goes wrong
- **Early exits**: Conditions that end the use case early

### 5. Define Preconditions

What must be true before this use case can start? Examples:
- "User is logged in"
- "Product exists in catalog"
- "User has sufficient account balance"

---

## File Naming Convention

Use descriptive, kebab-case names that reflect the use case title:

- ✅ `user-logs-in.md`
- ✅ `admin-creates-user.md`
- ✅ `system-processes-payment.md`
- ❌ `login.md` (too vague)
- ❌ `user_login.md` (use kebab-case)

---

## Use Cases and Roadmap Tasks

Use cases are the **source of truth** for what features should do. Roadmap tasks reference use cases:

```
### T-042: Implement user authentication

**Goal**: Users can log in to the system

**Use Case**: `docs/product/use-cases/user-logs-in.md`

**Acceptance Criteria**:
- [ ] User can log in with email and password
- [ ] System validates credentials
- [ ] User session is created
...
```

When implementing a feature:
1. Read the referenced use case(s)
2. Understand the goal and scenarios
3. Check architecture for constraints
4. Implement to satisfy the use case

---

## Use Case Relationships

Use cases can relate to each other:

- **Includes**: One use case always includes another (e.g., "User Places Order" includes "User Authenticates")
- **Extends**: One use case optionally extends another (e.g., "User Applies Discount" extends "User Places Order")
- **Generalizes**: A general use case is specialized (e.g., "User Pays with Credit Card" generalizes "User Pays")

Document these relationships in the "Related Use Cases" section.

---

## Best Practices

1. **One goal per use case**: If a use case has multiple goals, split it
2. **User perspective**: Write from the actor's point of view, not the system's
3. **Implementation-agnostic**: Don't mention UI elements, APIs, or technical details
4. **Complete scenarios**: Each use case should be a complete, testable story
5. **Keep it simple**: Start with the happy path, add extensions as needed
6. **Review regularly**: Use cases should evolve as understanding improves

---

## Template

See [TEMPLATE.md](./TEMPLATE.md) for a template you can copy when creating new use cases.

---

## Validation

Before a use case is used for development, it must be validated to ensure it meets quality standards.

**When to validate:**
- Before referencing in roadmap tasks
- When creating a new use case
- Before starting implementation (agents should validate)
- When reviewing PRs that add or modify use cases

**How to validate:**
1. Review against the checklist in [VALIDATION.md](./VALIDATION.md)
2. Use the validation prompt template for AI-assisted review
3. Fix any issues found
4. Mark as validated before proceeding

See [VALIDATION.md](./VALIDATION.md) for the complete validation guide, checklist, and examples.

---

## Examples

*Add links to example use cases here as they're created.*

