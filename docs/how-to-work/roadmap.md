# Roadmap

> **Document Type**: State (keep current)
> 
> Last updated: YYYY-MM-DD

---

## Current Focus

Complete initial project setup before starting feature development.

---

## In Progress

| ID | Task | Assignee | Branch | Notes |
|----|------|----------|--------|-------|
| | | | | |

---

## Up Next

Tasks ready to be picked up, in priority order.

### Project Setup (complete these first)

| ID | Task | Estimate | Dependencies |
|----|------|----------|--------------|
| T-001 | Define tech stack | S | None |
| T-002 | Document initial architecture | M | T-001 |
| T-003 | Set up local development environment | M | T-001 |
| T-004 | Configure test framework | S | T-003 |
| T-005 | Set up CI/CD pipeline | M | T-004 |
| T-006 | Configure deployment pipeline | M | T-005 |
| T-007 | Define coding conventions | S | T-001 |

### Feature Development

| ID | Task | Estimate | Dependencies |
|----|------|----------|--------------|
| | *Add your first features here* | | T-001 through T-007 |

---

## Backlog

Tasks that are defined but not yet prioritized.

| ID | Task | Notes |
|----|------|-------|
| | | |

---

## Completed

*Move tasks here when done. Include the PR number.*

| ID | Task | PR | Completed |
|----|------|----|-----------|
| | | | |

---

## Setup Task Details

### T-001: Define tech stack

**Goal**: Document all technology choices in `stack.md`.

**Acceptance Criteria**:
- [ ] Runtime and language defined
- [ ] Core framework(s) selected
- [ ] Database (if any) selected
- [ ] Testing tools selected
- [ ] Brief rationale for each choice

**Output**: Updated `docs/how-to-work/stack.md`

---

### T-002: Document initial architecture

**Goal**: Create a clear picture of how the system is structured.

**Acceptance Criteria**:
- [ ] High-level system diagram
- [ ] Main components identified
- [ ] Data flow documented
- [ ] Key boundaries defined

**Output**: Updated `docs/how-to-work/architecture.md`

---

### T-003: Set up local development environment

**Goal**: Anyone can clone the repo and run the project locally.

**Acceptance Criteria**:
- [ ] Dependencies can be installed with one command
- [ ] Dev server starts with one command
- [ ] Environment variables documented
- [ ] Setup instructions in `docs/local-development.md`

**Output**: Updated `docs/local-development.md`, working dev setup

---

### T-004: Configure test framework

**Goal**: Tests can be written and run consistently.

**Acceptance Criteria**:
- [ ] Test framework installed and configured
- [ ] At least one example test passing
- [ ] Test commands documented
- [ ] Coverage reporting set up

**Output**: Updated `docs/testing.md`, working test setup

---

### T-005: Set up CI/CD pipeline

**Goal**: Tests run automatically on every PR.

**Acceptance Criteria**:
- [ ] GitHub Actions (or equivalent) configured
- [ ] Tests run on PR creation
- [ ] Tests run on push to main/develop
- [ ] Build step included (if applicable)

**Output**: `.github/workflows/ci.yml` or equivalent

---

### T-006: Configure deployment pipeline

**Goal**: Code can be deployed to staging and production.

**Acceptance Criteria**:
- [ ] Deployment platform configured
- [ ] Staging environment set up
- [ ] Production environment set up
- [ ] Deployment process documented

**Output**: Updated `docs/deployment.md`, working deployments

---

### T-007: Define coding conventions

**Goal**: Consistent code style across the project.

**Acceptance Criteria**:
- [ ] Linter configured
- [ ] Formatter configured
- [ ] Pre-commit hooks (optional)
- [ ] Conventions documented

**Output**: Updated `docs/how-to-work/conventions.md`, config files

---

## Task Template

When adding a new task, include:

```
### T-XXX: Task Title

**Goal**: What should be true when this is done?

**Acceptance Criteria**:
- [ ] Criterion 1
- [ ] Criterion 2

**Technical Notes**: 
Any implementation hints or constraints

**References**:
- Related ADR: ADR-XXX (in docs/how-to-work/decisions.md)
- Related docs: docs/how-to-work/architecture.md#section
```
