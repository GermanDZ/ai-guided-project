# Rationale

> Why this template exists, the thinking behind it, and how to extend it.

---

## Overview

This template provides a documentation-driven workflow for software development that integrates human developers with AI agents (specifically Claude Code). It's built on Agile principles but adapted for a world where AI can handle implementation while humans focus on direction and decisions.

The goal is simple: **ship working software faster, with less friction, and maintain quality over time.**

---

## Core Concepts

### 1. Human-Agent Collaboration

**The problem**: AI coding assistants are powerful but work best with clear context. Without structure, you spend time re-explaining your project, architecture, and preferences in every session.

**The solution**: A documentation structure that serves as persistent context. The agent reads the docs, understands the project, and can start contributing immediately.

**How it works**:
- Human defines *what* to build and *why* (product direction, architecture decisions)
- Agent implements *how* (code, tests, refactoring)
- Both collaborate through conversation and small, reviewable PRs

This isn't about replacing developers—it's about amplifying them. The human remains in control of all meaningful decisions while delegating implementation details.

### 2. Documentation as Context, Not Bureaucracy

**The problem**: Documentation often becomes stale, ignored, or written for compliance rather than utility. Traditional docs are written for humans to read occasionally.

**The solution**: Documentation designed to be read by both humans and AI agents, frequently. Docs are the source of truth that enables autonomous work.

**Key insight**: When an AI agent can read your architecture doc and understand where to put new code, that doc is providing real value. When it can read your conventions and follow them without being told, documentation pays for itself.

**The two document types**:

| Type | Purpose | Update Pattern |
|------|---------|----------------|
| **State docs** | Current truth about the system | Overwrite when things change |
| **Incremental docs** | Historical record | Append-only, never modify past entries |

State docs answer "what is true now?" Incremental docs answer "how did we get here?"

### 3. Agile Principles Adapted

The Agile Manifesto was written for human teams. This template adapts it for human-agent collaboration:

| Original Value | Adaptation |
|----------------|------------|
| Individuals and interactions over processes and tools | Human judgment + agent capability over rigid automation |
| Working software over comprehensive documentation | Docs enable working software; they're not an end in themselves |
| Customer collaboration over contract negotiation | Conversation over specification; short feedback loops |
| Responding to change over following a plan | Roadmap is living; pivot when learning demands it |

**Principles in practice**:

- **Deliver value early and often**: Small PRs that ship working increments
- **Welcome change**: Requirements can change at any time; agent surfaces blockers early
- **Working software is the measure**: Every commit passes tests; every PR is deployable
- **Simplicity**: YAGNI by default; agent should push back on over-engineering
- **Reflect and adapt**: Retrospectives capture learning; workflow itself can evolve

### 4. Small PRs and Atomic Commits

**The problem**: Large PRs are hard to review, hard to debug, and hard to revert. They hide problems and slow down feedback.

**The solution**: Every PR solves exactly one issue. Commits within a PR follow a deliberate sequence.

**The commit strategy**:

```
1. Refactor/prepare (make room for the change)
2. Add tests (define expected behavior)
3. Implement (make tests pass)
4. Document (update relevant docs)
```

**Why this order matters**:
- Refactoring first means the actual feature commit is smaller and cleaner
- Tests first means you know when you're done
- Each commit passes tests, so you can bisect to find bugs
- Each commit is independently reviewable and revertable

**Why small PRs matter**:
- Faster reviews (reviewers can hold the whole change in their head)
- Faster feedback (less time waiting for review)
- Easier debugging (smaller surface area)
- Safer deployments (easier to roll back)

### 5. Stack-Agnostic Workflow

**The problem**: Most templates assume a specific technology. When you switch stacks, you lose your workflow.

**The solution**: Separate *how you work* from *what you build with*.

The `/docs/how-to-work` directory defines process and workflow. It works whether you're building with TypeScript, Python, Ruby, Go, Rust, Java, or anything else. The conventions, architecture, and stack docs are templates you fill in with your specific choices.

This means:
- Teams can share workflow practices across different projects
- Switching tech stacks doesn't mean reinventing your process
- The template works for web apps, APIs, CLIs, libraries, or any other software

---

## Document-by-Document Rationale

### Workflow Documents (`docs/how-to-work/`)

| Document | Why It Exists |
|----------|---------------|
| `agent.md` | The "how we work" guide. Ensures agents (and new humans) understand the collaboration model, commit strategy, and communication expectations. |
| `architecture.md` | Enables autonomous navigation. When an agent knows where components live and how they connect, it can make changes without asking for directions. |
| `stack.md` | Quick reference for technology choices. Prevents agents from suggesting incompatible libraries or patterns. |
| `conventions.md` | Consistency without constant correction. Agents follow naming, style, and testing conventions automatically. |
| `roadmap.md` | Single source for "what's next." Agents can pick up tasks without ambiguity about priorities. |
| `decisions.md` | Explains *why* things are the way they are. Prevents agents (and future humans) from "fixing" things that were intentional. |
| `changelog.md` | Human-readable history. Useful for releases, debugging, and understanding what changed when. |
| `glossary.md` | Domain terms defined once. Ensures consistent language across code, docs, and conversation. |
| `retrospectives.md` | Learning captured. Prevents repeating mistakes and surfaces what's working. |

### Project Documents (`docs/`)

| Document | Why It Exists |
|----------|---------------|
| `local-development.md` | Onboarding friction is real. A clear guide means anyone (human or agent) can get the project running quickly. |
| `testing.md` | Testing philosophy and commands in one place. Ensures consistent test coverage and makes CI debugging easier. |
| `deployment.md` | Deployment should be boring and repeatable. This doc makes it so. |

### Root Files

| File | Why It Exists |
|------|---------------|
| `README.md` | First impression and navigation hub. Points to everything else. |
| `CLAUDE.md` | Quick context for Claude Code. Avoids reading all docs for simple questions while pointing to full docs for implementation work. |
| `.env.example` | Documents required configuration without exposing secrets. |
| `.gitignore` | Comprehensive defaults for multiple languages. Less time fighting git. |
| `LICENSE` | Legal clarity. Placeholder reminds you to choose one. |

### GitHub Templates (`.github/`)

| File | Why It Exists |
|------|---------------|
| `PULL_REQUEST_TEMPLATE.md` | Consistent PR format. Links to issues, includes checklist, makes review easier. |
| `ISSUE_TEMPLATE/feature_request.md` | Structured feature requests with acceptance criteria. Reduces back-and-forth. |
| `ISSUE_TEMPLATE/bug_report.md` | Structured bug reports with reproduction steps. Faster debugging. |

---

## Extension Points

This template is a starting point, not a destination. Here's how to extend it:

### Adding New Document Types

**When to add a new doc**:
- You're repeatedly explaining the same thing
- Information exists but is scattered
- A new concern emerges that doesn't fit existing docs

**How to add**:
1. Decide if it's State or Incremental
2. Add to appropriate location (`docs/` or `docs/how-to-work/`)
3. Update `agent.md` if agents should read it
4. Update `README.md` documentation table

**Example extensions**:
- `docs/api.md` — API documentation for services
- `docs/how-to-work/security.md` — Security practices and requirements
- `docs/runbooks/` — Operational runbooks for incidents
- `docs/how-to-work/data-model.md` — Database schema and relationships

### Customizing for Team Size

**Solo developer**:
- Simplify PR process (self-review, faster merge)
- Focus on docs that help your future self and AI agents
- Retrospectives become personal journals

**Small team (2-5)**:
- Add code owners to enforce review
- Consider adding `CONTRIBUTING.md` for external contributors
- Retrospectives become team rituals

**Larger team**:
- Add team-specific conventions
- Consider splitting `roadmap.md` by team or domain
- Add ADR (Architecture Decision Record) templates with more formal review process
- Consider RFC (Request for Comments) process for significant changes

### Customizing for Project Type

**API/Backend**:
- Add `docs/api.md` for endpoint documentation
- Add `docs/how-to-work/data-model.md` for schema
- Extend testing.md with API testing patterns

**Frontend/UI**:
- Add `docs/design-system.md` for component library
- Add `docs/how-to-work/accessibility.md` for a11y requirements
- Consider Storybook or similar for component documentation

**Library/Package**:
- Add `docs/api-reference.md` for public API
- Add `docs/migration.md` for version upgrades
- Focus `README.md` on installation and usage

**Monorepo**:
- Add per-package READMEs
- Consider `docs/packages/` structure
- Extend `architecture.md` with package relationships

### Integrating with External Tools

**Project Management (Jira, Linear, etc.)**:
- Link `roadmap.md` tasks to external tickets
- Consider making roadmap.md a view into external system rather than source of truth

**CI/CD**:
- Add `.github/workflows/` templates
- Document CI/CD in `deployment.md`
- Consider adding `docs/how-to-work/ci.md` for pipeline conventions

**Monitoring/Observability**:
- Add `docs/observability.md` for logging, metrics, tracing conventions
- Add runbooks for common alerts

**Feature Flags**:
- Add `docs/feature-flags.md` for flag conventions
- Document flag lifecycle in `conventions.md`

### Adding Automation

**Pre-commit hooks**:
- Lint and format on commit
- Run affected tests
- Validate commit message format

**PR automation**:
- Auto-label based on files changed
- Auto-assign reviewers
- Require linked issues

**Doc generation**:
- Generate API docs from code
- Generate changelog from commits
- Validate doc links aren't broken

---

## Philosophy

### Why Documentation-Driven?

Code is the ultimate source of truth for *what* the system does. But code can't tell you:
- Why it was built this way
- What alternatives were considered
- What the intended behavior is (vs. accidental)
- How components are meant to work together
- What's planned for the future

Documentation fills these gaps. When documentation is designed for both humans and AI agents, it becomes infrastructure rather than overhead.

### Why Agile?

Agile isn't about sprints, standups, or story points. It's about:
- Delivering value early and often
- Embracing change as learning
- Prioritizing working software
- Enabling sustainable pace

These principles work regardless of team size, technology, or whether your teammate is human or AI.

### Why Small PRs?

The research is clear: smaller changes are:
- Reviewed faster and more thoroughly
- Less likely to introduce bugs
- Easier to debug when bugs occur
- Safer to deploy and roll back

The discipline of small PRs also forces clarity of thought. If you can't explain a change in a small PR, you probably don't understand it well enough.

### Why Stack-Agnostic?

Technology choices change. Good process principles don't. By separating workflow from technology, this template:
- Works across your entire portfolio
- Survives technology migrations
- Enables knowledge transfer between projects

---

## Credits and Inspiration

This template draws from:
- **Agile Manifesto** — Core values and principles
- **Architectural Decision Records (ADRs)** — Michael Nygard's pattern for documenting decisions
- **Keep a Changelog** — Changelog format and philosophy
- **Conventional Commits** — Commit message structure
- **Ship Small** — The discipline of small, reviewable changes
- **Docs as Code** — Treating documentation with the same rigor as code

---

## Feedback and Evolution

This template is itself subject to the principles it espouses:
- It should evolve based on experience
- Changes should be small and incremental
- What works should be kept; what doesn't should be changed

If something isn't working, change it. If something is missing, add it. The goal is a workflow that helps you ship better software faster—not adherence to a template.
