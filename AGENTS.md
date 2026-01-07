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

This project uses a documentation-driven workflow. Before implementing:

1. Read `docs/how-to-work/agent.md` for collaboration guidelines
2. Read `docs/how-to-work/stack.md` for technology choices
3. Read `docs/how-to-work/architecture.md` for system design
4. Read `docs/how-to-work/conventions.md` for coding standards
5. Check `docs/how-to-work/roadmap.md` for current tasks

### Key Principles

- **Small PRs**: Each PR solves exactly one issue
- **Atomic commits**: Each commit does one thing and passes all tests
- **Refactor first**: Preparation commits before feature commits
- **Working software**: Every commit is deployable
- **Simplicity**: YAGNI—don't over-engineer

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

When implementing a feature, follow this order:

1. `refactor`: Prepare codebase for changes
2. `test`: Add tests for new functionality
3. `feat`/`fix`: Implement the actual change
4. `docs`: Update documentation

Each commit must pass all tests.

### Pull Requests

- Title: `[TYPE] Brief description (#issue)`
- Link to the issue being solved
- Include brief description of approach
- Keep PRs small and focused (<400 lines changed)

---

## Testing

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

1. Check `docs/how-to-work/decisions.md` for past architectural decisions
2. Check `docs/how-to-work/glossary.md` for domain terminology
3. Ask for clarification rather than assuming
4. Surface trade-offs and propose alternatives

---

## Additional Resources

- [Workflow Guide](docs/how-to-work/agent.md)
- [Architecture](docs/how-to-work/architecture.md)
- [Tech Stack](docs/how-to-work/stack.md)
- [Conventions](docs/how-to-work/conventions.md)
- [Roadmap](docs/how-to-work/roadmap.md)
