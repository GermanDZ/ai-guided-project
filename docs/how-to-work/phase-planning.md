# Phase Planning and Management

> How to plan and track work using the Unified Process phase structure

---

## ⚠️ MANDATORY: Phase Planning Is Always Active

**This is not optional documentation - it is the core workflow for this project.**

### Critical Requirements

1. **All work MUST be done within a phase context**
   - No feature work without an active phase plan
   - No iteration work without a defined roadmap
   - No deliverables without outputs.md tracking

2. **Phase plans MUST be up-to-date**
   - Roadmaps updated weekly during active work
   - Status changes tracked immediately
   - Artifacts tracked as they're produced

3. **Agents MUST check phase status before any work**
   - First action: Determine current phase
   - Check current iteration in phase roadmap
   - Verify task exists in roadmap before implementing
   - Update roadmap after completing work (with permission)

4. **Projects MUST start with Inception phase**
   - Cannot skip directly to Construction
   - Each phase must be completed before the next
   - Phase transitions require formal sign-off

**If you are an AI agent and phase plans don't exist, you MUST stop and request the human create them before proceeding with any implementation work.**

---

## Overview

This project follows the **Unified Process (UP)** methodology with four main phases:

1. **Inception** - Define project scope, vision, and feasibility
2. **Elaboration** - Establish architecture, detailed requirements, and risk mitigation
3. **Construction** - Build production-ready features iteratively
4. **Transition** - Deploy, train users, and transition to production

Each phase consists of multiple **iterations** (typically 1-4 weeks each), and each iteration delivers working software.

### Phase Progression

```
START → Inception → Elaboration → Construction → Transition → END
          ↓            ↓              ↓              ↓
      (Plan +)    (Plan +)       (Plan +)       (Plan +)
      (Execute)   (Execute)      (Execute)      (Execute)
```

**You cannot skip phases. Each must be completed with sign-off before moving to the next.**

---

## Directory Structure

```
docs/plans/
├── _TEMPLATE_roadmap.md     # Template for phase roadmaps
├── _TEMPLATE_outputs.md      # Template for phase outputs/artifacts
├── inception/
│   ├── roadmap.md           # Inception phase iteration plan
│   └── outputs.md           # Expected artifacts for Inception
├── elaboration/
│   ├── roadmap.md           # Elaboration phase iteration plan
│   └── outputs.md           # Expected artifacts for Elaboration
├── construction/
│   ├── roadmap.md           # Construction phase iteration plan
│   └── outputs.md           # Expected artifacts for Construction
└── transition/
    ├── roadmap.md           # Transition phase iteration plan
    └── outputs.md           # Expected artifacts for Transition
```

---

## Agent Workflow: Phase-First Approach

### Before Starting ANY Work

**Every AI agent MUST follow this checklist before implementing anything:**

```
□ Step 1: Check if phase plans exist
   → If NO phase plans exist: STOP and request human create Inception phase
   → If phase plans exist: Continue to Step 2

□ Step 2: Identify current phase
   → Read all phase roadmaps to find which has status "In Progress"
   → Current phase = the one with active iterations
   → If no active phase: Request human to start Inception

□ Step 3: Identify current iteration
   → Open current phase's roadmap.md
   → Find iteration with status "In Progress"
   → This is your work context

□ Step 4: Check if task exists in roadmap
   → Look in current iteration's "Planned Work" table
   → Find task that matches what you're being asked to do
   → If task doesn't exist: Ask human to add it to roadmap first

□ Step 5: Read referenced use cases
   → Check "Use Cases Addressed" in iteration
   → Read those use case files for requirements
   → Ensure you understand acceptance criteria

□ Step 6: Check required artifacts
   → Open current phase's outputs.md
   → Identify artifacts related to your task
   → Note acceptance criteria you must meet

□ Step 7: Proceed with implementation
   → Follow TDD workflow
   → Create commits following conventions
   → Track progress mentally for later roadmap update

□ Step 8: Request roadmap update (after completion)
   → Ask permission to update roadmap.md
   → Ask permission to update outputs.md
   → Never update without explicit approval
```

### Example Agent Start Sequence

```markdown
Agent receives request: "Implement user login feature"

Agent thinks:
1. ✓ Check phase plans exist
   → Found docs/plans/construction/roadmap.md

2. ✓ Identify current phase
   → Construction phase, status: In Progress

3. ✓ Identify current iteration
   → Iteration 2: "User Authentication", status: In Progress

4. ✓ Check task exists
   → Found T-042: "Implement user login" in Planned Work table

5. ✓ Read use cases
   → UC-002: User Login defines requirements

6. ✓ Check artifacts
   → outputs.md requires: Test Suite, Working Software

7. ✓ Proceed with TDD
   → Write tests, implement feature

8. ✓ Request update
   → "Should I update the roadmap to mark T-042 as complete?"
```

### What If Phase Plans Don't Exist?

**Agent response template:**

```
I notice that phase planning documents don't exist yet for this project.

According to the workflow, all work must be done within a phase context,
and projects must start with the Inception phase.

Would you like me to help you initialize the Inception phase by:
1. Copying the templates to docs/plans/inception/
2. Helping you define the initial phase goals and iterations?

Or would you prefer to create the phase plans yourself first?

Until phase plans are in place, I cannot proceed with implementation work.
```

### Starting a New Project: Inception First

**When a project has no phase plans, the human must:**

1. **Initialize Inception phase**
   ```bash
   cp docs/plans/_TEMPLATE_roadmap.md docs/plans/inception/roadmap.md
   cp docs/plans/_TEMPLATE_outputs.md docs/plans/inception/outputs.md
   ```

2. **Define Inception goals** in `roadmap.md`
   - What is the project vision?
   - What are the key use cases?
   - What are the major risks?
   - What needs to be proven feasible?

3. **Define Inception outputs** in `outputs.md`
   - Vision document
   - Initial use case model
   - Risk assessment
   - Business case
   - Initial architecture

4. **Plan first iteration** (1-2 weeks)
   - Break Inception goals into tasks
   - Assign priorities
   - Set dates

5. **Commit the plan**
   ```bash
   git add docs/plans/inception/
   git commit -m "docs(planning): initialize Inception phase"
   ```

6. **Now agents can work** - Phase context exists!

---

## Files and Their Purpose

### roadmap.md

**Purpose**: Detailed iteration planning and tracking for a phase

**Contains**:
- Phase overview and goals
- Success criteria
- Individual iteration plans with tasks
- Tracking information (dates, status, assignments)
- Progress updates and lessons learned
- Phase summary

**Used by**: Everyone planning and executing work

**Update frequency**:
- Weekly during active iterations
- At iteration boundaries (start/end)
- When significant changes occur

### outputs.md

**Purpose**: Define expected artifacts and deliverables for a phase

**Contains**:
- Required artifacts for the phase
- Optional artifacts
- Acceptance criteria for each artifact
- Quality standards
- Sign-off requirements

**Used by**: Everyone to understand what needs to be delivered

**Update frequency**:
- Created at phase start
- Updated when artifacts are completed
- Reviewed at phase exit

---

## Procedure: Starting a New Phase

### Step 1: Copy Templates

```bash
# For the phase you're starting (e.g., inception)
cp docs/plans/_TEMPLATE_roadmap.md docs/plans/inception/roadmap.md
cp docs/plans/_TEMPLATE_outputs.md docs/plans/inception/outputs.md
```

### Step 2: Define Expected Outputs

Edit `outputs.md` for your phase:

1. **Review phase-specific artifacts** in the template
   - Inception: Vision, use cases, risks, business case
   - Elaboration: Architecture, detailed use cases, executable baseline
   - Construction: Working software, tests, documentation
   - Transition: Production release, training, support docs

2. **Customize artifact requirements**
   - Add project-specific artifacts
   - Remove irrelevant ones
   - Set priorities (Critical/High/Medium/Low)
   - Define acceptance criteria
   - Assign owners

3. **Set quality standards**
   - Test coverage thresholds
   - Documentation requirements
   - Performance criteria
   - Security requirements

4. **Define exit criteria**
   - What must be complete to exit this phase?
   - Who must approve?
   - What metrics must be met?

**Example** (Inception outputs.md):

```markdown
### 1. Vision Document

**Type**: Document
**Priority**: Critical
**Owner**: Product Owner
**Status**: Not Started

#### Content Requirements
- Project purpose and stakeholders
- Key features (high-level)
- Success metrics
- Constraints and assumptions

#### Acceptance Criteria
- [ ] Stakeholders have reviewed and agreed
- [ ] Scope boundaries clearly defined
- [ ] Success criteria are measurable
```

### Step 3: Plan Iterations in Roadmap

Edit `roadmap.md` for your phase:

1. **Set phase information**
   - Phase name and dates
   - Overall phase goals
   - Success criteria
   - Key deliverables (reference outputs.md)

2. **Break work into iterations**
   - Typical iteration: 1-4 weeks
   - Each iteration should deliver something testable
   - Early iterations: high-risk items
   - Later iterations: lower-risk items

3. **For each iteration, define**:
   - **Goals**: What will be achieved
   - **Tasks**: Specific work items with IDs
   - **Use cases**: Which use cases are addressed
   - **Risks**: Risks specific to this iteration
   - **Tracking info**: Dates, assignments, effort estimates

**Example** (Inception iteration):

```markdown
### Iteration 1: Establish Project Foundation

**Duration**: 1 week
**Start**: 2026-01-13 | **End**: 2026-01-20
**Status**: Not Started

#### Goals
- Define project vision and scope
- Identify key stakeholders
- List critical use cases

#### Planned Work
| ID | Task | Type | Priority | Assigned To | Estimated Effort |
|----|------|------|----------|-------------|------------------|
| T-001 | Draft vision document | Docs | High | Product Owner | 2d |
| T-002 | Identify stakeholders | Docs | High | Product Owner | 1d |
| T-003 | List 10 key use cases | Docs | High | Product Owner | 2d |

#### Use Cases Addressed
- UC-001: User registration (identified)
- UC-002: User login (identified)
```

### Step 4: Link Roadmap to Outputs

In `roadmap.md`, reference specific artifacts from `outputs.md`:

```markdown
### Key Deliverables

Reference `outputs.md` for detailed artifact descriptions.

- Vision Document (see outputs.md #1)
- Initial Use Case Model (see outputs.md #2)
- Glossary (see outputs.md #3)
```

This creates traceability: roadmap shows when work happens, outputs define what "done" means.

---

## Procedure: Executing an Iteration

### At Iteration Start

1. **Review iteration goals** in `roadmap.md`
2. **Check artifact requirements** in `outputs.md`
3. **Update task status** to "In Progress"
4. **Create feature branches** for tasks
5. **Break tasks into subtasks** if needed (can use `docs/how-to-work/roadmap.md` for detailed task tracking)

### During Iteration

1. **Work on tasks** using TDD (see `docs/how-to-work/tdd.md`)
2. **Update roadmap.md weekly**:
   - Mark completed tasks
   - Update status
   - Note blockers or issues
3. **Track artifact progress** in `outputs.md`:
   - Update status (Not Started → In Progress → Completed)
   - Update progress percentages
   - Check off acceptance criteria as met
4. **Create PRs** for completed work
5. **Update use case documentation** as features are built

### At Iteration End

1. **Update "Actual Progress" section** in `roadmap.md`:
   - Completion date
   - Achievements
   - Issues encountered
   - Lessons learned
   - Velocity (tasks or story points completed)

2. **Review artifacts** in `outputs.md`:
   - Which artifacts are complete?
   - What's their status?
   - Do they meet acceptance criteria?

3. **Demo working software** to stakeholders

4. **Retrospective**:
   - What went well?
   - What could improve?
   - Action items for next iteration

---

## Procedure: Completing a Phase

### Phase Exit Review

1. **Review outputs.md**:
   - [ ] All critical artifacts completed?
   - [ ] Acceptance criteria met?
   - [ ] Quality standards satisfied?
   - [ ] Artifacts reviewed and approved?

2. **Review roadmap.md**:
   - [ ] All iterations completed?
   - [ ] Phase goals achieved?
   - [ ] Success criteria met?
   - [ ] Lessons learned documented?

3. **Complete "Phase Summary"** section in `roadmap.md`:
   - List achievements
   - Record metrics (velocity, test coverage, etc.)
   - List produced artifacts
   - Document lessons learned
   - Create action items for next phase

4. **Get sign-offs** in `outputs.md`:
   - Project Lead
   - Tech Lead
   - Product Owner
   - QA Lead (if applicable)

### Phase Transition Checklist

**MANDATORY: Complete ALL items before moving to the next phase**

#### Exit Current Phase

- [ ] All iterations in phase completed
- [ ] All critical artifacts in outputs.md marked "Completed"
- [ ] All acceptance criteria met
- [ ] Phase Summary section in roadmap.md filled out
- [ ] Lessons learned documented
- [ ] Metrics recorded (velocity, coverage, defects)
- [ ] Sign-offs obtained from all required approvers
- [ ] Outstanding issues documented and assigned to future phases
- [ ] Git commits and branches cleaned up

#### Phase-Specific Exit Criteria

**Exiting Inception:**
- [ ] Vision document approved by stakeholders
- [ ] Key use cases identified (20-30% detailed)
- [ ] Major risks identified and mitigation strategies defined
- [ ] Business case demonstrates project viability
- [ ] Initial architecture approach agreed upon
- [ ] Feasibility proven (technical and business)
- [ ] Elaboration phase planned

**Exiting Elaboration:**
- [ ] Software architecture documented and stable
- [ ] Use cases detailed (80-90% complete)
- [ ] Executable architecture baseline working
- [ ] Major technical risks mitigated
- [ ] Requirements baselined
- [ ] Test strategy defined
- [ ] Construction phase planned with realistic estimates

**Exiting Construction:**
- [ ] All planned use cases implemented
- [ ] Production-ready software built
- [ ] Comprehensive test suite passing (meets coverage thresholds)
- [ ] User documentation complete
- [ ] Deployment package ready
- [ ] Performance requirements met
- [ ] Security requirements met
- [ ] Transition phase planned

**Exiting Transition:**
- [ ] Software deployed to production
- [ ] Users trained
- [ ] Support processes in place
- [ ] Post-deployment issues resolved
- [ ] Project closure report complete
- [ ] Maintenance plan defined

#### Enter Next Phase

- [ ] Review action items from completed phase
- [ ] Copy templates for next phase
- [ ] Define next phase goals and success criteria
- [ ] Define next phase outputs and artifacts
- [ ] Plan first iteration of next phase
- [ ] Commit phase plans to git
- [ ] Communicate phase transition to team
- [ ] Update project roadmap (`docs/how-to-work/roadmap.md`)

#### Document Phase Transition

In the completed phase's `roadmap.md`, add:

```markdown
## Phase Transition

**Completed**: YYYY-MM-DD
**Transitioned to**: [Next Phase]
**Approved by**: [Names and roles]

### Transition Notes
- Key achievements carried forward
- Deferred items moved to [next phase]
- Action items: [list]
```

### Transition to Next Phase

**After completing the checklist above:**

1. **Review action items** from completed phase
2. **Start next phase** (follow "Starting a New Phase" procedure)
3. **Carry forward** any deferred artifacts or tasks
4. **Update project roadmap** to reflect phase completion
5. **Archive** completed phase documentation (keep in git history)

**Remember: You cannot skip phases. Each phase builds on the previous one.**

---

## Using Roadmaps as Input for Work

### For Developers

**Before starting work**:

1. Read current phase's `roadmap.md`
2. Find your current iteration
3. Check your assigned tasks
4. Review use cases referenced
5. Check `outputs.md` for artifact requirements

**When implementing a task**:

1. Read referenced use case(s) in `docs/product/use-cases/`
2. Check if task requires artifact creation (see `outputs.md`)
3. Follow TDD workflow (see `docs/how-to-work/tdd.md`)
4. Update roadmap.md when task is complete

**Example workflow**:

```bash
# 1. Check current iteration
cat docs/plans/construction/roadmap.md | grep -A 20 "In Progress"

# 2. See task T-042 assigned to you: "Implement user login"
# 3. Check use case
cat docs/product/use-cases/UC-002-user-login.md

# 4. Check if artifacts needed
cat docs/plans/construction/outputs.md | grep -i "login"

# 5. Implement using TDD
# 6. Update roadmap when done
```

### For AI Agents

**When asked to work on a feature**:

```markdown
Agent workflow:
1. Check `docs/plans/{current_phase}/roadmap.md` for context
2. Find relevant iteration and tasks
3. Read referenced use cases
4. Check `docs/plans/{current_phase}/outputs.md` for artifact requirements
5. Implement following TDD
6. **ASK PERMISSION** before updating roadmap
7. Update roadmap only if human approves
```

**Important**: Agents must ALWAYS ask permission before updating roadmap or outputs files.

### For Project Managers

**Planning**:
- Use `roadmap.md` to schedule work
- Use `outputs.md` to define deliverables
- Track progress in both files

**Reporting**:
- Use "Actual Progress" sections for status reports
- Use "Artifacts Produced" for deliverable tracking
- Use metrics in "Phase Summary" for velocity tracking

---

## Integration with Other Documentation

### Relationship to docs/how-to-work/roadmap.md

The project also has `docs/how-to-work/roadmap.md` for overall project planning.

**Differences**:
- **Phase roadmaps** (`docs/plans/{phase}/roadmap.md`): Detailed iteration plans for a specific phase
- **Project roadmap** (`docs/how-to-work/roadmap.md`): High-level features and tasks across all phases

**How they work together**:
1. Project roadmap defines high-level features
2. Phase roadmaps break features into iterations and tasks
3. Phase roadmaps track detailed progress
4. Project roadmap gets updated when phases complete

**Example**:
- Project roadmap: "Sprint 1: User Authentication (Inception phase)"
- Inception roadmap: "Iteration 1: Define auth use cases, Iteration 2: Prototype login flow"

### Relationship to Use Cases

- **Use cases** define WHAT features should do
- **Roadmaps** define WHEN features will be built
- **Outputs** define HOW features will be documented/delivered

**Workflow**:
1. Use case is identified (Inception)
2. Use case is detailed (Elaboration)
3. Use case is implemented (Construction)
4. Each step tracked in phase roadmaps
5. Implementation artifacts tracked in outputs.md

---

## Example: Complete Phase Flow

### Scenario: Starting Elaboration Phase

**1. Define outputs** (`docs/plans/elaboration/outputs.md`):

```markdown
### 1. Software Architecture Document
**Priority**: Critical
**Status**: Not Started

#### Content Requirements
- Architectural patterns (MVC, layered, etc.)
- Technology stack decisions
- Component diagram
- Deployment architecture

#### Acceptance Criteria
- [ ] Tech lead has reviewed
- [ ] Addresses top 5 architectural risks
- [ ] Includes working code example
```

**2. Plan iterations** (`docs/plans/elaboration/roadmap.md`):

```markdown
### Iteration 1: Establish Architecture

**Duration**: 2 weeks
**Goals**:
- Create architectural baseline
- Mitigate top technical risks
- Build executable skeleton

#### Planned Work
| ID | Task | Type | Priority | Assigned To | Estimated Effort |
|----|------|------|----------|-------------|------------------|
| T-010 | Write architecture doc | Docs | High | Tech Lead | 3d |
| T-011 | Setup project structure | Refactor | High | Dev Team | 2d |
| T-012 | Implement auth skeleton | Feature | High | Dev 1 | 5d |
```

**3. Execute iteration**:
- Dev team works on tasks
- Architecture doc created and reviewed
- Auth skeleton implemented using TDD
- Weekly updates to roadmap.md

**4. Iteration end**:
- Update "Actual Progress" in roadmap.md
- Update artifact status in outputs.md
- Demo auth skeleton
- Retrospective and lessons learned

**5. Phase end** (after 4 iterations):
- Complete "Phase Summary" in roadmap.md
- Verify all artifacts in outputs.md
- Get sign-offs
- Prepare for Construction phase

---

## Best Practices

### Do's

- ✓ Keep roadmap.md updated weekly
- ✓ Reference use cases in iteration plans
- ✓ Break work into small, testable tasks
- ✓ Track lessons learned after each iteration
- ✓ Link roadmap tasks to artifacts in outputs.md
- ✓ Use consistent task IDs (T-001, T-002, etc.)
- ✓ Celebrate achievements in phase summaries

### Don'ts

- ✗ Don't let roadmap get stale (update regularly)
- ✗ Don't skip iteration retrospectives
- ✗ Don't define artifacts without acceptance criteria
- ✗ Don't move to next phase without sign-offs
- ✗ Don't plan too far ahead (1-2 iterations at a time)
- ✗ Don't update roadmap without team awareness
- ✗ Agents: Don't update roadmap without human permission

---

## Quick Reference

### When to use each file:

| Task | File to Check | Section |
|------|---------------|---------|
| "What am I working on this iteration?" | `{phase}/roadmap.md` | Current iteration → Planned Work |
| "What needs to be delivered this phase?" | `{phase}/outputs.md` | Required Artifacts |
| "What use case am I implementing?" | `{phase}/roadmap.md` | Iteration → Use Cases Addressed |
| "What does 'done' mean for this artifact?" | `{phase}/outputs.md` | Artifact → Acceptance Criteria |
| "When is this phase ending?" | `{phase}/roadmap.md` | Phase Overview → Target End Date |
| "What are the phase goals?" | `{phase}/roadmap.md` | Phase Overview → Phase Goals |
| "Who needs to review this artifact?" | `{phase}/outputs.md` | Artifact → Review Process |
| "What did we learn last iteration?" | `{phase}/roadmap.md` | Iteration → Actual Progress → Lessons Learned |

---

## Templates Usage

### Creating a new phase plan:

```bash
# Copy templates
cp docs/plans/_TEMPLATE_roadmap.md docs/plans/inception/roadmap.md
cp docs/plans/_TEMPLATE_outputs.md docs/plans/inception/outputs.md

# Edit for your phase
vim docs/plans/inception/roadmap.md
vim docs/plans/inception/outputs.md

# Commit
git add docs/plans/inception/
git commit -m "docs(planning): add Inception phase plan"
```

### Updating during work:

```bash
# Update roadmap with progress
vim docs/plans/construction/roadmap.md

# Update artifact status
vim docs/plans/construction/outputs.md

# Commit changes
git add docs/plans/construction/
git commit -m "docs(planning): update Construction iteration 2 progress"
```

---

## Questions?

If you're unsure about:
- **What phase you're in**: Check git branch or ask project lead
- **What to work on next**: Check current iteration in `roadmap.md`
- **What deliverables are needed**: Check `outputs.md`
- **Whether to update roadmap**: If you're an AI agent, always ask first

For more information:
- See `docs/how-to-work/agent.md` for overall workflow
- See `docs/how-to-work/tdd.md` for development practices
- See `docs/product/use-cases/README.md` for feature requirements
