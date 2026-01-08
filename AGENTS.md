# AGENTS.md

> Instructions for AI coding agents working on this project.
> 
> This file follows the [AGENTS.md](https://agents.md) open standard and works with Claude Code, Cursor, Copilot, Codex, Jules, Windsurf, and other AI coding tools.

---

## Project Overview

*One paragraph describing what this project does, who it's for, and its primary purpose.*

---

## Quick Start

```bash
# Clone and enter project
git clone <repository-url>
cd <project-name>

# Install dependencies
# [Add your command: npm install, pip install -r requirements.txt, etc.]

# Start development server
# [Add your command: npm run dev, python manage.py runserver, etc.]

# Run tests
# [Add your command: npm test, pytest, go test ./..., etc.]
```

---

## Workflow

This project uses a documentation-driven workflow with **Unified Process** phase management.

### ⚠️ MANDATORY: Phase-First Workflow

**ALL work must be done within a phase context. No exceptions.**

#### Before ANY Implementation

AI agents MUST follow this sequence:

1. **Check phase plans exist** - Look for `docs/plans/{phase}/roadmap.md` files
   - If NO phase plans exist: STOP and request human initialize Inception phase
   - Cannot proceed without phase context

2. **Identify current phase** - Find which phase has status "In Progress"
   - Projects start with Inception → Elaboration → Construction → Transition
   - Cannot skip phases

3. **Check current iteration** - Find iteration with status "In Progress" in current phase roadmap
   - All work happens within an iteration
   - Cannot work outside iteration context

4. **Verify task exists** - Confirm task is listed in iteration's "Planned Work" table
   - If task missing: Request human add it to roadmap first
   - Cannot implement unplanned tasks

5. **Only then proceed** with reading documentation and implementing

#### Required Documentation Reading Order

Once phase context is confirmed, read in this order:

1. `docs/how-to-work/phase-planning.md` - **MANDATORY** phase workflow
2. Current phase `docs/plans/{phase}/roadmap.md` - Current iteration tasks
3. Current phase `docs/plans/{phase}/outputs.md` - Required deliverables
4. `docs/product/use-cases/README.md` - How features are defined
5. Use case(s) referenced in your task - Feature requirements
6. `docs/how-to-work/agent.md` - Collaboration guidelines
7. `docs/how-to-work/stack.md` - Technology choices
8. `docs/how-to-work/architecture.md` - System design
9. `docs/how-to-work/conventions.md` - Coding standards
10. `docs/how-to-work/tdd.md` - Test-driven development practice
11. `docs/how-to-work/roadmap.md` - High-level project roadmap

**Critical Rules**:
- Use cases are the source of truth for what features should do
- Phase roadmaps define WHEN work happens
- Phase outputs define WHAT artifacts are required
- All three must align for any implementation work

### Key Principles

- **Small PRs**: Each PR solves exactly one issue
- **Atomic commits**: Each commit does one thing and passes all tests
- **Test-Driven Development**: Write tests first (RED), make them pass (GREEN), then refactor
- **Refactor first**: Preparation commits before feature commits
- **Working software**: Every commit is deployable
- **Simplicity**: YAGNI—don't over-engineer

### Task Completion

After completing a task, iteration, or sprint:

1. **Always ask permission first** - Never update roadmaps without explicit human approval
2. **Request roadmap update** - Ask the human if you should update roadmap files
3. **What to update** (if permission granted):

   **For phase roadmaps** (`docs/plans/{phase}/roadmap.md`):
   - Update "Actual Progress" section in iteration
   - Mark completed tasks in "Planned Work" table
   - Document lessons learned
   - Update iteration status

   **For project roadmap** (`docs/how-to-work/roadmap.md`):
   - Move completed tasks from "In Progress" or "Up Next" to "Completed"
   - Include task ID, description, PR number, and completion date
   - For sprints, summarize what was completed

   **For phase outputs** (`docs/plans/{phase}/outputs.md`):
   - Update artifact status (In Progress → Completed)
   - Check off acceptance criteria
   - Update progress percentages

Roadmap and planning documents are state documents that must stay current, but updates require human oversight.

---

## Commands

### Development

```bash
# Install dependencies
# [Add your command]

# Start development server
# [Add your command]

# Build for production
# [Add your command]
```

### Testing

```bash
# Run all tests
# [Add your command]

# Run tests in watch mode
# [Add your command]

# Run tests with coverage
# [Add your command]

# Run a specific test
# [Add your command]
```

### Linting & Formatting

```bash
# Lint code
# [Add your command]

# Format code
# [Add your command]

# Type check (if applicable)
# [Add your command]
```

### Database (if applicable)

```bash
# Run migrations
# [Add your command]

# Rollback migrations
# [Add your command]

# Seed database
# [Add your command]
```

---

## Code Style

### General

- Prefer clarity over cleverness
- Keep functions small and focused
- Write self-documenting code
- Comment *why*, not *what*

### Naming

*Define your conventions. Examples:*

- Variables: `camelCase` / `snake_case`
- Functions: `camelCase` / `snake_case`
- Classes/Types: `PascalCase`
- Constants: `SCREAMING_SNAKE_CASE`

### Imports

*Define import ordering:*

1. Standard library
2. External dependencies
3. Internal modules
4. Relative imports

---

## Git Conventions

### Branches

```
feature/issue-{number}-{short-description}
fix/issue-{number}-{short-description}
refactor/{description}
docs/{description}
```

### Commit Messages

```
type(scope): description

Types: feat, fix, refactor, test, docs, chore
```

### Commit Sequence

When implementing a feature using TDD, follow this order:

1. `refactor`: Prepare codebase for changes (all tests GREEN)
2. `test`: Add failing test for next requirement (RED)
3. `feat`/`fix`: Implement code to pass test (GREEN)
4. `refactor`: Clean up code (still GREEN)
5. Repeat steps 2-4 for each requirement
6. `docs`: Update documentation

Each GREEN commit must pass all tests. RED commits may have failing tests (the new ones only).

### Pull Requests

- Title: `[TYPE] Brief description (#issue)`
- Link to the issue being solved
- Include brief description of approach
- Keep PRs small and focused (<400 lines changed)

---

## Testing

This project uses **Test-Driven Development (TDD)** for building features. See `docs/how-to-work/tdd.md` for detailed guidance.

### TDD Cycle

```
RED → GREEN → REFACTOR
```

1. **RED**: Write a failing test
2. **GREEN**: Write simplest code to pass
3. **REFACTOR**: Clean up while keeping tests green

### What to Test

- Business logic and data transformations
- Edge cases and error handling
- Public APIs and interfaces
- Integration points

### Test Naming

Use descriptive names:

```
Good: test_returns_empty_list_when_no_items_match_filter
Bad:  test_filter_works
```

---

## Architecture

*Brief overview of system structure. See `docs/how-to-work/architecture.md` for details.*

### Key Directories

```
src/            # Source code
tests/          # Test files
docs/           # Documentation
  how-to-work/  # Workflow docs (read these first)
  plans/        # Phase-based iteration planning
    inception/  # Inception phase roadmap and outputs
    elaboration/  # Elaboration phase roadmap and outputs
    construction/  # Construction phase roadmap and outputs
    transition/  # Transition phase roadmap and outputs
  product/      # Product documentation (use cases, features)
```

### Important Patterns

*List key patterns used in this codebase.*

---

## Security Considerations

- Never commit secrets or credentials
- Use environment variables for configuration
- Validate all user input
- Follow principle of least privilege

---

## When Stuck

1. Check the relevant use case(s) in `docs/product/use-cases/` for feature requirements
2. Check `docs/how-to-work/decisions.md` for past architectural decisions
3. Check `docs/how-to-work/glossary.md` for domain terminology
4. Ask for clarification rather than assuming
5. Surface trade-offs and propose alternatives

---

## Additional Resources

### Core Workflow
- [Workflow Guide](docs/how-to-work/agent.md) - How to work with humans and other agents
- [Phase Planning](docs/how-to-work/phase-planning.md) - Unified Process phase and iteration management
- [Test-Driven Development](docs/how-to-work/tdd.md) - TDD practice and examples

### Planning & Requirements
- [Project Roadmap](docs/how-to-work/roadmap.md) - High-level project plan
- [Phase Roadmaps](docs/plans/) - Detailed iteration plans by phase
- [Use Cases](docs/product/use-cases/README.md) - Source of truth for product features

### Technical
- [Architecture](docs/how-to-work/architecture.md) - System design and patterns
- [Tech Stack](docs/how-to-work/stack.md) - Technology choices
- [Conventions](docs/how-to-work/conventions.md) - Coding standards
