# Quick Start: Initialize Your First Phase

> Get your project started with Inception phase planning

---

## For New Projects: Start Here

If you're starting a new project and need to set up phase planning for the first time, follow these steps.

### Step 1: Copy Inception Templates (30 seconds)

```bash
# From project root
cp docs/plans/_TEMPLATE_roadmap.md docs/plans/inception/roadmap.md
cp docs/plans/_TEMPLATE_outputs.md docs/plans/inception/outputs.md
```

### Step 2: Edit Inception Roadmap (15-30 minutes)

Open `docs/plans/inception/roadmap.md` and fill in:

#### Phase Overview

```markdown
## Phase Overview

### Phase Goals

Define project scope and vision, validate feasibility, identify major risks.

### Success Criteria

- [ ] Vision document approved by stakeholders
- [ ] Key use cases identified (20-30% detailed)
- [ ] Major risks documented with mitigation plans
- [ ] Technical feasibility proven
- [ ] Business case demonstrates project value
```

#### Iteration 1 (Typical: 1-2 weeks)

```markdown
### Iteration 1: Vision and Scope

**Duration**: 1 week
**Start**: 2026-01-13 | **End**: 2026-01-20
**Status**: In Progress

#### Goals

- Define project vision and scope
- Identify stakeholders
- List critical use cases

#### Planned Work

| ID | Task | Type | Priority | Assigned To | Estimated Effort |
|----|------|------|----------|-------------|------------------|
| T-001 | Draft vision document | Docs | High | Product Owner | 2d |
| T-002 | Identify key stakeholders | Docs | High | Product Owner | 0.5d |
| T-003 | List 10 critical use cases | Docs | High | Team | 2d |
| T-004 | Setup development environment | Chore | High | Tech Lead | 1d |
| T-005 | Create initial project structure | Chore | High | Tech Lead | 1d |
```

### Step 3: Edit Inception Outputs (10-15 minutes)

Open `docs/plans/inception/outputs.md` and customize the required artifacts.

Key artifacts for Inception:

```markdown
### 1. Vision Document

**Type**: Document
**Priority**: Critical
**Status**: Not Started

#### Content Requirements
- Project purpose and goals
- Key stakeholders
- High-level features (3-5 main capabilities)
- Success metrics
- Constraints and assumptions

#### Acceptance Criteria
- [ ] Stakeholders reviewed and approved
- [ ] Scope boundaries clearly defined
- [ ] Success criteria measurable
- [ ] Aligned with business objectives
```

Typical Inception outputs:
- Vision Document
- Initial Use Case Model (identify 10-20 use cases)
- Glossary (domain terms)
- Risk List (top 5-10 risks)
- Business Case
- Initial Architecture Notebook
- Development Environment Setup

### Step 4: Commit Your Plan

```bash
git add docs/plans/inception/
git commit -m "docs(planning): initialize Inception phase"
```

### Step 5: Start Working!

Now AI agents can work on your project. They'll:
1. Check `docs/plans/inception/roadmap.md` for current iteration
2. Pick tasks from "Planned Work" table
3. Implement following TDD
4. Update roadmap when complete (with your permission)

---

## Example: Minimal Inception Plan

Here's a bare-minimum Inception phase plan to get started quickly:

### Roadmap (docs/plans/inception/roadmap.md)

```markdown
# Inception Phase Roadmap

> Phase: Inception
> Start Date: 2026-01-13
> Target End Date: 2026-01-27
> Status: In Progress

## Phase Overview

### Phase Goals

- Define project vision and validate feasibility
- Identify key use cases
- Assess major risks
- Setup development environment

### Success Criteria

- [ ] Vision document complete
- [ ] 10 use cases identified
- [ ] Development environment working
- [ ] Top 5 risks documented

### Key Deliverables

- Vision Document
- Initial Use Case List
- Risk Assessment
- Working Development Environment

---

## Iterations

### Iteration 1: Foundation

**Duration**: 2 weeks
**Start**: 2026-01-13 | **End**: 2026-01-27
**Status**: In Progress

#### Goals

- Create vision document
- Identify core use cases
- Setup project infrastructure

#### Planned Work

| ID | Task | Type | Priority | Assigned To | Estimated Effort |
|----|------|------|----------|-------------|------------------|
| T-001 | Write vision document | Docs | High | Product Lead | 2d |
| T-002 | Identify 10 key use cases | Docs | High | Product Lead | 2d |
| T-003 | Document top 5 project risks | Docs | Med | Tech Lead | 1d |
| T-004 | Setup dev environment | Chore | High | Tech Lead | 1d |
| T-005 | Create project skeleton | Chore | High | Dev Team | 2d |

#### Use Cases Addressed

- Will be identified in T-002

#### Risks & Mitigations

| Risk | Impact | Probability | Mitigation |
|------|--------|-------------|------------|
| Unclear requirements | High | Medium | Weekly stakeholder reviews |
| Technical complexity | High | Low | Proof of concept in Elaboration |
```

### Outputs (docs/plans/inception/outputs.md)

```markdown
# Inception Phase Outputs

> Phase: Inception
> Expected Duration: 2 weeks

## Required Artifacts

### 1. Vision Document

**Type**: Document
**Priority**: Critical
**Status**: Not Started

#### Content Requirements
- Project purpose and stakeholders
- Key features (high-level)
- Success metrics

#### Acceptance Criteria
- [ ] Stakeholders reviewed
- [ ] Scope defined
- [ ] Metrics measurable

### 2. Initial Use Case Model

**Type**: Document
**Priority**: Critical
**Status**: Not Started

#### Content Requirements
- List of 10-20 use cases
- Brief description of each
- Priority ranking

#### Acceptance Criteria
- [ ] Covers main user workflows
- [ ] Prioritized by business value

### 3. Risk List

**Type**: Document
**Priority**: High
**Status**: Not Started

#### Content Requirements
- Top 5-10 project risks
- Impact and probability assessment
- Mitigation strategies

#### Acceptance Criteria
- [ ] Major risks identified
- [ ] Mitigation plan for each

### 4. Development Environment

**Type**: Code/Config
**Priority**: Critical
**Status**: Not Started

#### Content Requirements
- Project structure
- Build system
- Test framework
- Development tools configured

#### Acceptance Criteria
- [ ] Team members can run project locally
- [ ] CI/CD pipeline working
- [ ] Tests can be executed
```

---

## Checklist: Ready to Start Inception

Before beginning Inception phase:

- [ ] Templates copied to `docs/plans/inception/`
- [ ] Roadmap has at least one iteration defined
- [ ] Iteration has status "In Progress"
- [ ] Iteration has at least 3-5 tasks in Planned Work table
- [ ] Outputs defines minimum 3-4 required artifacts
- [ ] Plans committed to git
- [ ] Team knows phase has started

Once these are complete, agents can begin working!

---

## After Inception: Moving to Elaboration

When Inception iteration(s) are complete:

1. **Complete Phase Summary** in `roadmap.md`
2. **Get sign-offs** in `outputs.md`
3. **Follow Phase Transition Checklist** in `docs/how-to-work/phase-planning.md`
4. **Copy templates** for Elaboration phase
5. **Plan Elaboration** iterations with focus on:
   - Detailed use cases (80-90% complete)
   - Architecture design
   - Risk mitigation
   - Executable architecture baseline

---

## Common Questions

### Q: Do I need to plan all iterations upfront?

**A:** No! Plan 1-2 iterations at a time. Add more iterations as you complete earlier ones.

### Q: How long should Inception be?

**A:** Typically 1-4 weeks, depending on project size. For small projects, even 1 week can be enough.

### Q: Can I skip Inception and go straight to Construction?

**A:** No. Inception validates feasibility and defines scope. Skipping it leads to unclear requirements and wasted effort.

### Q: What if my project already has code?

**A:** Start with Inception anyway to document vision, use cases, and risks. Then move to Elaboration to document architecture.

### Q: Do agents really enforce this?

**A:** Yes. Agents following this workflow will refuse to implement features without phase context.

---

## Help

- **Full documentation**: See `docs/how-to-work/phase-planning.md`
- **Templates**: Located in `docs/plans/_TEMPLATE_*.md`
- **Questions**: Ask your AI agent or project lead
