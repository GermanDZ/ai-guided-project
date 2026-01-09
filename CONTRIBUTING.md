# Contributing Guide

This guide explains how to contribute to this project, with sections for both human contributors and AI assistants.

---

## Quick Start

1. Check `docs/how-to-work/roadmap.md` for available tasks
2. Pick one task to work on
3. Create a branch and implement
4. Submit a PR solving exactly that one task

---

## For Human Contributors

### Getting Started

1. **Review the documentation:**
   - Read `docs/how-to-work/agent.md` for the workflow
   - Review `docs/how-to-work/architecture.md` for system design
   - Check `docs/how-to-work/roadmap.md` for current priorities

2. **Set up your environment:**
   - Follow instructions in `README.md`
   - Ensure tests pass before making changes

3. **Recommended VSCode Extensions:**
   - `bierner.markdown-mermaid` - Preview Mermaid diagrams in markdown

### Making Changes

#### 1. Create a Branch

```bash
git checkout -b feature/issue-{number}-{short-description}
# or
git checkout -b fix/issue-{number}-{short-description}
```

**Branch naming:**
- `feature/` - New functionality
- `fix/` - Bug fixes
- `docs/` - Documentation only
- `refactor/` - Code improvements
- `test/` - Test additions/improvements

#### 2. Work on ONE Task

Each PR should solve exactly one item from the roadmap. This keeps changes:
- Easy to review
- Easy to revert if needed
- Easy to understand

#### 3. Follow Standards

- **Code:** Follow style guide in `docs/how-to-work/conventions.md`
- **Tests:** Write tests for new functionality
- **Documentation:** Update as you go
- **Commits:** Write clear commit messages

#### 4. Create a Pull Request

**PR Checklist:**
- [ ] Tests added/updated and passing
- [ ] Documentation updated if needed
- [ ] Code follows style guide
- [ ] PR solves exactly one roadmap item
- [ ] Self-reviewed the diff

---

## For AI Assistants

### Your Role

You are a **development assistant**. Your role is to:
- Implement tasks from the roadmap
- Generate tests
- Update documentation
- Assist with code review
- Help with refactoring

Your role is NOT to:
- Make architectural decisions without human approval
- Skip tests or documentation
- Change multiple unrelated things in one PR

### Before Starting Any Task

1. **Read the roadmap** - `docs/how-to-work/roadmap.md`
2. **Understand the architecture** - `docs/how-to-work/architecture.md`
3. **Check conventions** - `docs/how-to-work/conventions.md`
4. **Ask questions** if anything is unclear

### During Implementation

**Always:**
- Follow existing code patterns
- Write tests alongside code
- Handle errors appropriately
- Update relevant documentation

**Never:**
- Work on multiple roadmap items at once
- Make assumptions about unclear requirements
- Skip error handling
- Leave TODO comments without creating issues

### File Reading Priority

When given a task, read files in this order:

1. **Roadmap** - `docs/how-to-work/roadmap.md` (find your task)
2. **Architecture** - `docs/how-to-work/architecture.md` (constraints)
3. **Existing Code** - `/src/[related-modules]/` (patterns to follow)
4. **Tests** - `/tests/[related-tests]/` (test patterns)

---

## Development Workflow

```
1. Pick ONE task from roadmap
   ↓
2. Create feature branch
   ↓
3. Implement with tests
   ↓
4. Self-review changes
   ↓
5. Create pull request
   ↓
6. Address review feedback
   ↓
7. Merge when approved
```

---

## Code Standards

### General Principles

1. **Clarity over cleverness** - Write code that's easy to understand
2. **Consistency** - Follow existing patterns
3. **Simplicity** - YAGNI (You Aren't Gonna Need It)

### Error Handling

```typescript
// Good: Specific errors
throw new ValidationError('Email is required');

// Bad: Generic errors
throw new Error('Error');
```

### Code Comments

```typescript
// Good: Explain WHY, not WHAT
// Using exponential backoff to handle rate limiting
await retryWithBackoff(apiCall);

// Bad: Explain WHAT (code already shows this)
// Call the retry function
await retryWithBackoff(apiCall);
```

---

## Getting Help

- **Architecture questions:** Review ADRs in `docs/how-to-work/decisions.md`
- **Process questions:** Read `docs/how-to-work/agent.md`
- **Quick decisions:** Check `docs/project/decisions-log.md`

If something is unclear, ask rather than assume.
