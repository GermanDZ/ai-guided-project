# Conventions

> **Document Type**: State (keep current)
> 
> Last updated: YYYY-MM-DD
>
> **Note**: This template is stack-agnostic. Fill in conventions specific to your chosen language and framework.

---

## File Structure

```
project-root/
├── docs/
│   ├── how-to-work/        # Workflow documentation
│   └── ...                 # Project-specific docs
├── src/                    # Source code (adjust to your stack)
├── tests/                  # Test files
└── ...
```

*Customize based on your stack's conventions (e.g., `app/` for Rails, `pkg/` for Go, `lib/` for Rust, `src/main/java` for Java).*

---

## Naming Conventions

*Define conventions for your stack. Examples:*

### Files

| Type | Convention | Example |
|------|------------|---------|
| *Components/Modules* | *PascalCase / snake_case* | *UserProfile.tsx / user_profile.rb* |
| *Utilities* | *camelCase / snake_case* | *formatDate.ts / format_date.py* |
| *Tests* | *Match source + test suffix* | *user_test.go / user.spec.ts* |

### Code

| Type | Convention | Example |
|------|------------|---------|
| *Variables* | *camelCase / snake_case* | *userName / user_name* |
| *Functions/Methods* | *camelCase / snake_case* | *getUserById / get_user_by_id* |
| *Classes/Types* | *PascalCase* | *UserService* |
| *Constants* | *SCREAMING_SNAKE* | *MAX_RETRIES* |

---

## Code Style

### General Principles

- Prefer clarity over cleverness
- Keep functions small and focused
- Use meaningful names
- Write self-documenting code; add comments for *why*, not *what*

### Language-Specific

*Add your stack's style rules here. Common examples:*

```
# JavaScript/TypeScript
- Prefer `const` over `let`
- Use explicit return types on public functions
- Prefer named exports

# Python
- Follow PEP 8
- Use type hints
- Prefer f-strings

# Ruby
- Follow Ruby Style Guide
- Prefer symbols over strings for hash keys
- Use guard clauses

# Go
- Follow Effective Go
- Use gofmt
- Keep interfaces small

# Rust
- Use rustfmt
- Prefer &str over String for parameters
- Handle all errors explicitly

# Java
- Follow Google Java Style Guide
- Use final where applicable
- Prefer composition over inheritance
```

### Imports / Dependencies

*Define import ordering for your stack. General pattern:*

```
# 1. Standard library / built-ins
# 2. External dependencies / third-party
# 3. Internal / project modules
# 4. Relative imports
```

---

## Git Conventions

### Branches

```
feature/issue-{number}-{short-description}
fix/issue-{number}-{short-description}
refactor/{description}
docs/{description}
```

### Commits

```
type(scope): description

Types: feat, fix, refactor, test, docs, chore
```

### PRs

- Title: `[TYPE] Brief description (#issue)`
- Always link to the issue/task being solved
- Include a brief description of the approach

---

## Testing

### What to Test

- Business logic and data transformations
- Edge cases and error handling
- Public APIs and interfaces
- Integration points

### What to Skip

- Third-party library internals
- Trivial getters/setters
- Implementation details

### Test Naming

Use descriptive names that explain the scenario:

```
Good: test_returns_empty_list_when_no_items_match_filter
Bad:  test_filter_works
```

---

## Documentation

### Code Comments

- Explain *why*, not *what*
- Document non-obvious behavior
- Use your language's doc format (JSDoc, docstrings, rustdoc, godoc, Javadoc, etc.)

### Docs Folder

- Keep docs up to date when making changes
- Reference docs in PR descriptions when relevant
