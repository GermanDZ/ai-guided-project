# Test-Driven Development (TDD)

> **Document Type**: State (keep current)
>
> Last updated: 2026-01-08

---

## What is TDD?

Test-Driven Development (TDD) is a software development practice where you write tests *before* writing the implementation code. It follows a simple, repetitive cycle that ensures code quality, correctness, and maintainability.

### The TDD Cycle: Red-Green-Refactor

```
RED → GREEN → REFACTOR → RED → GREEN → REFACTOR → ...
```

1. **RED**: Write a failing test
   - Write a test for the next bit of functionality you want to add
   - Run the test and watch it fail (it should fail because the functionality doesn't exist yet)
   - If the test passes immediately, it's not testing anything new

2. **GREEN**: Make the test pass
   - Write the *simplest* code that makes the test pass
   - Don't worry about perfection—just make it work
   - Use hard-coded values if necessary; you'll refactor next

3. **REFACTOR**: Improve the code
   - Clean up the code while keeping tests green
   - Remove duplication
   - Improve names
   - Simplify logic
   - Tests protect you—if they still pass, your refactor is safe

---

## Why TDD?

### Benefits

1. **Design feedback**: Writing tests first forces you to think about the API/interface before implementation
2. **Regression safety**: Every feature has tests from day one
3. **Documentation**: Tests show *how* code is meant to be used
4. **Confidence**: Refactoring is safe when tests exist
5. **Focus**: You only write code needed to pass tests (YAGNI enforced)
6. **Debugging**: When a test fails, you know exactly what broke

### What TDD Is Not

- TDD is not "write all tests first, then implement everything"
- TDD is not a substitute for integration or end-to-end tests
- TDD is not about 100% code coverage
- TDD is not slow—it prevents debugging sessions that waste time

---

## TDD in Practice

### Step-by-Step Example

Let's implement a function that validates email addresses.

#### Step 1: RED - Write a failing test

```javascript
// email.test.js
describe('isValidEmail', () => {
  it('returns true for valid email addresses', () => {
    expect(isValidEmail('user@example.com')).toBe(true);
  });
});
```

Run the test → It fails (function doesn't exist yet) ✓

#### Step 2: GREEN - Make it pass

```javascript
// email.js
export function isValidEmail(email) {
  return true; // Simplest code that makes the test pass
}
```

Run the test → It passes ✓

#### Step 3: Add another test (RED)

```javascript
// email.test.js
it('returns false for invalid email addresses', () => {
  expect(isValidEmail('not-an-email')).toBe(false);
});
```

Run the test → It fails (our function always returns true) ✓

#### Step 4: GREEN - Make both tests pass

```javascript
// email.js
export function isValidEmail(email) {
  return email.includes('@');
}
```

Run tests → Both pass ✓

#### Step 5: REFACTOR (if needed)

```javascript
// email.js
const EMAIL_REGEX = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;

export function isValidEmail(email) {
  return EMAIL_REGEX.test(email);
}
```

Run tests → Still pass ✓

#### Step 6: Continue the cycle

Add more test cases (empty string, null, spaces, etc.) and evolve the implementation.

---

## TDD Rules

### The Three Laws of TDD (Bob Martin)

1. **Don't write production code** until you have a failing test
2. **Don't write more of a test** than is sufficient to fail
3. **Don't write more production code** than is sufficient to pass the test

### Practical Guidelines

1. **Start with the simplest case**
   - Don't tackle the hardest scenario first
   - Build complexity gradually

2. **One test at a time**
   - Write one test, make it pass, then write the next test
   - Don't write multiple failing tests at once

3. **Test behavior, not implementation**
   - Test what the code does, not how it does it
   - This allows refactoring without breaking tests

4. **Keep tests fast**
   - Fast tests = fast feedback
   - Slow tests discourage running them frequently

5. **Keep tests isolated**
   - Each test should be independent
   - Tests should not depend on execution order

6. **Use descriptive test names**
   - Test names should explain what's being tested
   - Good: `test_returns_error_when_user_not_found`
   - Bad: `test_user_error`

---

## TDD and the Commit Sequence

TDD fits naturally into our atomic commit workflow:

```
1. [refactor] Prepare code structure (tests still pass)
2. [test] Add failing tests for new functionality (RED)
3. [feat] Implement feature to make tests pass (GREEN)
4. [refactor] Clean up implementation (REFACTOR)
5. [docs] Update documentation
```

### Example Commit Sequence

Implementing a user registration feature:

```bash
# Setup phase (all tests passing)
git commit -m "refactor(auth): extract user validation utilities"

# TDD cycle begins
git commit -m "test(auth): add tests for user registration validation"
# Tests fail at this point (RED)

git commit -m "feat(auth): implement basic user registration"
# Tests now pass (GREEN)

git commit -m "refactor(auth): simplify validation logic"
# Tests still pass (REFACTOR)

git commit -m "test(auth): add tests for duplicate email handling"
# New test fails (RED)

git commit -m "feat(auth): prevent duplicate email registration"
# All tests pass (GREEN)

git commit -m "docs(auth): update API documentation"
```

Each commit represents a safe checkpoint where all tests pass (except the RED commits, which are allowed to have failing tests as long as they're the *new* tests you just added).

---

## TDD Patterns

### Test Data Builders

Use builders to create test data cleanly:

```javascript
// Bad
const user = { id: 1, name: 'Alice', email: 'alice@example.com', age: 30, role: 'admin', ... };

// Good
const user = userBuilder().withRole('admin').build();
```

### Arrange-Act-Assert (AAA)

Structure tests clearly:

```javascript
it('calculates total price with tax', () => {
  // Arrange
  const cart = new ShoppingCart();
  cart.addItem({ price: 100 });

  // Act
  const total = cart.getTotalWithTax(0.1);

  // Assert
  expect(total).toBe(110);
});
```

### Test Doubles

Use mocks, stubs, and fakes judiciously:

```javascript
// Stub an external API
const weatherService = {
  getCurrentTemperature: () => 72
};

const recommendation = getClothingRecommendation(weatherService);
expect(recommendation).toBe('Light jacket');
```

---

## When Not to Use TDD

TDD is not always the right tool. Skip it when:

1. **Exploring/prototyping**: When you don't know what you're building yet
2. **Trivial code**: Getters, setters, simple data structures
3. **UI layout**: Visual positioning is better tested with visual regression tools
4. **Performance optimization**: Profile first, optimize second
5. **Learning**: When learning a new API, experimentation in a REPL is faster

In these cases, write tests *after* the code stabilizes.

---

## TDD and Documentation

### Tests as Specification

Well-written tests serve as living documentation:

```javascript
describe('UserService.register', () => {
  it('creates a new user with valid data', () => { ... });
  it('returns error when email is already taken', () => { ... });
  it('returns error when password is too weak', () => { ... });
  it('sends a welcome email after registration', () => { ... });
});
```

Reading these tests tells you:
- What the `register` method does
- What inputs it accepts
- What edge cases it handles
- What side effects it produces

### Updating Tests with Code

When requirements change:
1. Update the test first (it will fail)
2. Update the implementation
3. Tests pass again

This ensures tests and code never drift out of sync.

---

## TDD Quick Reference

### Starting a New Feature

```
1. Read the use case (what should this do?)
2. Think about the simplest test case
3. Write that test (it will fail)
4. Write minimal code to pass it
5. Refactor if needed
6. Repeat for next case
```

### When Stuck

```
1. Am I trying to test too much at once? (break it down)
2. Is this test testing behavior? (not implementation)
3. Have I written the simplest code? (don't over-engineer)
4. Do I need to refactor before adding more? (clean as you go)
```

### Before Committing

```
1. Are all tests passing? (green state)
2. Have I refactored duplication? (clean code)
3. Are test names descriptive? (documentation)
4. Is this commit atomic? (one logical change)
```

---

## Integration with Agent Workflow

When implementing features using TDD:

1. **Plan phase**: Identify test cases from use cases
2. **Implementation phase**: Follow RED-GREEN-REFACTOR for each test case
3. **Commit phase**: Each GREEN state is a potential commit point
4. **Review phase**: Tests serve as specification documentation

**Example session:**

```
Human: Implement password validation from use case UC-003

Agent: I'll use TDD to implement password validation. Based on UC-003, I need to test:
1. Minimum length (8 characters)
2. Requires at least one uppercase letter
3. Requires at least one number
4. Requires at least one special character

I'll start with the simplest test case and work through each requirement.

[Commits RED test for minimum length]
[Commits GREEN implementation]
[Commits REFACTOR if needed]
[Repeats for each requirement]

All tests passing. Ready for review.
```

---

## Resources

- *Test Driven Development: By Example* by Kent Beck
- *Growing Object-Oriented Software, Guided by Tests* by Steve Freeman & Nat Pryce
- Martin Fowler's articles on testing: https://martinfowler.com/testing/

---

## Summary

TDD is about:
- **Rhythm**: RED → GREEN → REFACTOR
- **Confidence**: Tests protect your code
- **Design**: Tests first = better APIs
- **Simplicity**: Only write code that passes tests
- **Documentation**: Tests show how code is used

Not a silver bullet, but a powerful practice for building reliable, maintainable software step by step.
