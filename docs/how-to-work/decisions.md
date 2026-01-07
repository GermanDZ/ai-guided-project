# Architectural Decision Records

> **Document Type**: Incremental (append-only)
> 
> New decisions are added at the bottom. Past decisions are never modified—add a new decision that supersedes if needed.

---

## ADR-001: Use ADRs for Architectural Decisions

**Date**: YYYY-MM-DD

**Status**: Accepted

### Context

We need a way to document architectural decisions so that future team members (and AI agents) understand why the system is built the way it is.

### Decision

We will use Architectural Decision Records (ADRs) stored in this file. Each decision is numbered sequentially and includes context, the decision made, and consequences.

### Consequences

- Historical decisions are preserved and searchable
- New team members can understand the evolution of the architecture
- Decisions cannot be silently changed—superseding requires a new ADR

---

## Template for New Decisions

<!--
Copy this template when adding a new decision:

## ADR-XXX: Title

**Date**: YYYY-MM-DD

**Status**: Proposed | Accepted | Superseded by ADR-XXX | Deprecated

### Context

What is the issue that we're seeing that is motivating this decision?

### Decision

What is the change that we're proposing and/or doing?

### Consequences

What becomes easier or more difficult because of this decision?
-->
