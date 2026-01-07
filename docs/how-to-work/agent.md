# Agent Workflow Guide

This document defines how AI agents (Claude Code) should interact with this project's documentation and development workflow.

---

## Philosophy: Agile with Agents

This workflow adapts the Agile Manifesto for human-agent collaboration. The human defines *what* and *why*; the agent implements *how*—but always in tight feedback loops.

### Core Values (adapted)

| We value... | Over... | In practice |
|-------------|---------|-------------|
| **Human judgment + agent capability** | Rigid process | The human steers; the agent executes. Either can flag when something feels wrong. |
| **Working software** | Comprehensive docs | Docs exist to enable working software, not as an end. Ship early, learn, iterate. |
| **Conversation over specification** | Detailed upfront specs | Short feedback loops. Agent asks questions. Human reviews small PRs. |
| **Responding to change** | Following the plan | Roadmap is a living document. Pivot when learning demands it. |

### Principles in Action

1. **Deliver value early and often**
   - Small PRs that ship working increments
   - Each PR solves one user-facing or technical need
   - Prefer a working slice over a complete layer

2. **Welcome change**
   - Requirements in `roadmap.md` can change at any time
   - Agent should never "go dark" for long—surface blockers and pivots early
   - Past decisions (`decisions.md`) can be superseded, not silently ignored

3. **Working software is the measure**
   - Every commit passes tests
   - Every PR is deployable
   - Docs update *after* code works, not before

4. **Sustainable pace**
   - Small, reviewable PRs reduce cognitive load
   - Atomic commits make debugging and reverting easy
   - Refactor continuously—don't let debt accumulate

5. **Technical excellence enables agility**
   - Clean code is easier to change
   - Tests are not optional—they enable fearless refactoring
   - Simple solutions over clever ones

6. **Simplicity: maximize work not done**
   - Before implementing, ask: "Is this necessary?"
   - YAGNI (You Aren't Gonna Need It) by default
   - Agent should push back on over-engineering

7. **Reflect and adapt**
   - `retrospectives.md` captures what we learn
   - Workflow itself can change based on experience
   - Agent can suggest process improvements

### The Human-Agent Contract

**Human responsibilities:**
- Define *what* to build and *why* (product direction)
- Make architectural and design decisions (or delegate explicitly)
- Review PRs—agent work doesn't merge without human approval
- Update priorities when they change

**Agent responsibilities:**
- Implement *how* within the defined architecture
- Ask clarifying questions before going deep
- Surface trade-offs and alternatives
- Keep PRs small and reviewable
- Maintain test coverage and code quality

**Shared:**
- Either party can propose changes to architecture, workflow, or priorities
- Decisions are documented, not assumed
- Trust, but verify (hence PR reviews)

---

## Documentation Structure

All workflow documentation lives in `/docs/how-to-work`. Documents are categorized by their update pattern:

### Incremental Documents (append-only)

These documents grow over time. New entries are added without modifying previous content. They serve as a historical record.

| Document | Purpose |
|----------|---------|
| `decisions.md` | Architectural Decision Records (ADRs). Each decision is numbered and dated. Never modify past decisions—add new ones that supersede if needed. |
| `changelog.md` | Human-readable history of significant changes. Follows Keep a Changelog format. |
| `retrospectives.md` | Post-sprint or post-milestone reflections. What worked, what didn't, lessons learned. |

### State Documents (current truth)

These documents reflect the current state of the project. They should be updated to stay accurate. Agents use these as context.

| Document | Purpose |
|----------|---------|
| `architecture.md` | System design, component relationships, data flow. The source of truth for how the system is structured. |
| `stack.md` | Technology choices with brief rationale. Versions, frameworks, tools. |
| `roadmap.md` | Current priorities and upcoming work. Tasks and issues to be implemented. |
| `conventions.md` | Coding standards, naming conventions, file structure rules. |
| `glossary.md` | Domain terms and their definitions. |

---

## Agent Context Loading

When starting a session, agents should read these documents in order:

1. `docs/how-to-work/agent.md` (this file) — understand the workflow
2. `docs/how-to-work/stack.md` — understand the technology
3. `docs/how-to-work/architecture.md` — understand the system design
4. `docs/how-to-work/conventions.md` — understand coding standards
5. `docs/how-to-work/roadmap.md` — understand current priorities

For specific tasks, also consult:
- `docs/how-to-work/decisions.md` — for context on why things are the way they are
- `docs/how-to-work/glossary.md` — for domain terminology

---

## Development Workflow

### Branch Strategy

```
main
 └── feature/issue-{number}-{short-description}
 └── fix/issue-{number}-{short-description}
 └── refactor/{short-description}
```

### The Small PR Philosophy

Every PR should be:
- **Focused**: Solves exactly one issue or task from `roadmap.md`
- **Reviewable**: Small enough to review in one sitting (aim for <400 lines changed)
- **Complete**: All tests pass, no broken functionality

### Commit Strategy

Commits within a PR follow a deliberate sequence:

```
1. [refactor] Prepare codebase for new feature
2. [refactor] Extract shared utilities
3. [test] Add tests for upcoming functionality
4. [feat] Implement the actual feature
5. [docs] Update documentation
```

#### Commit Rules

1. **Atomic**: Each commit does one thing
2. **Green**: Every commit passes all tests (`git stash && npm test` should pass)
3. **Ordered**: Refactors and preparation come before new functionality
4. **Minimal diff**: Each commit changes only what's necessary for its purpose

#### Commit Message Format

```
type(scope): brief description

- Detail about what changed
- Why it changed (if not obvious)

Refs #issue-number
```

Types: `feat`, `fix`, `refactor`, `test`, `docs`, `chore`

---

## Task Execution Process

When asked to implement a feature or fix:

### 1. Understand

- Read the relevant issue/task in `roadmap.md`
- Check `decisions.md` for related architectural context
- Review `architecture.md` to understand affected components
- **Ask questions if anything is unclear**—don't assume

### 2. Plan

Before writing code, outline:
- What's the smallest working increment? (Agile: deliver value early)
- What refactoring is needed first?
- What tests need to be added or modified?
- What's the minimal set of changes? (Simplicity principle)
- Is this actually necessary? (YAGNI check)

Share this plan for approval before proceeding. **This is a conversation, not a specification.**

### 3. Implement (commit by commit)

**Goal: Working software at every step.**

```
Phase 1: Preparation
  - Refactor existing code to make room for changes
  - Each refactor is a separate commit
  - Run tests after each commit ← non-negotiable

Phase 2: Foundation
  - Add new tests (they may fail initially)
  - Add any new utilities or helpers needed
  - Keep it simple—add only what's necessary

Phase 3: Implementation
  - Implement the feature/fix
  - Make tests pass
  - Working software is the measure of progress

Phase 4: Documentation
  - Update relevant docs
  - Add to changelog if significant
  - Docs follow code, not the reverse
```

**If requirements change mid-implementation:** Stop, acknowledge, adapt. This is expected and welcome.

### 4. Review Preparation

Before requesting review:
- Rebase on latest main if needed
- Ensure all commits are atomic and pass tests
- Write a clear PR description linking to the issue

---

## Documentation Updates

### When to Update State Documents

| Event | Documents to Update |
|-------|-------------------|
| New technology added | `stack.md` |
| Architecture changed | `architecture.md`, possibly `decisions.md` |
| New conventions established | `conventions.md` |
| Task completed | `roadmap.md` (mark done), `changelog.md` |
| New domain term introduced | `glossary.md` |

### When to Add to Incremental Documents

| Event | Document | Action |
|-------|----------|--------|
| Significant architectural choice made | `decisions.md` | Add new ADR |
| Version released or milestone reached | `changelog.md` | Add new entry |
| Sprint/phase completed | `retrospectives.md` | Add reflection |

---

## Communication Style

**Conversation over documentation.** These guidelines support collaboration, not bureaucracy.

1. **Short feedback loops**: Don't go dark. Share progress, ask questions, surface blockers early.

2. **Ask before large changes**: If a task requires more than ~5 commits, discuss the plan first.

3. **Challenge when appropriate**: If a requirement seems unnecessary or over-engineered, say so. Simplicity matters.

4. **Surface trade-offs**: When making decisions, briefly explain alternatives considered.

5. **Propose improvements**: If you see a better way to do something—code, process, or architecture—suggest it.

6. **Reference docs**: When your work relates to existing decisions or architecture, cite the relevant doc.

---

## Example Session

```
Human: Implement the user authentication feature from the roadmap

Agent: I'll implement user authentication. Let me first review the relevant docs...

[reads docs/how-to-work/architecture.md, stack.md, roadmap.md]

Based on the architecture, I'll need to:
1. Refactor the middleware structure to support auth hooks
2. Add the auth utilities and types
3. Implement the auth middleware
4. Add the login/logout endpoints
5. Update docs

Here's my proposed commit sequence:
1. refactor(middleware): extract base middleware class
2. refactor(types): add user and session types  
3. test(auth): add auth middleware tests
4. feat(auth): implement JWT-based auth middleware
5. feat(api): add login and logout endpoints
6. docs: update architecture and changelog

Does this approach look right before I proceed?
```

---

## Quick Reference

### Before Starting Any Task
```
1. Read: docs/how-to-work/agent.md → stack.md → architecture.md → roadmap.md
2. Identify: Which issue/task am I solving?
3. Ask: Is anything unclear? Is this actually needed? (YAGNI)
4. Plan: What's my commit sequence? What's the smallest working increment?
5. Confirm: Get approval on the plan (conversation, not contract)
```

### Before Each Commit
```
1. Is this atomic? (one logical change)
2. Do tests pass? (working software at every step)
3. Is the commit message clear?
4. Is this the simplest solution? (maximize work not done)
```

### Before Requesting Review
```
1. All commits pass tests individually?
2. PR solves exactly one issue?
3. Is it the smallest shippable increment?
4. Docs updated if needed?
5. PR description links to issue?
```

### When Blocked or Uncertain
```
1. Ask immediately—don't assume
2. Surface trade-offs you're seeing
3. Propose alternatives if you have them
4. Welcome the answer changing your direction
```
