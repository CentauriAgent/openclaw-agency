# Agent Teams Skill

Coordinate multiple specialized agents working together on complex tasks using Beads for task management and state tracking.

## Overview

This skill enables team-based development where a lead agent orchestrates specialized worker agents. Each agent focuses on their expertise while Beads handles:
- Task tracking with dependencies
- Agent state management  
- Work assignment (slots)
- Async coordination (gates)

## Quick Start

Tell the lead agent: **"Build X as a team"** or **"Use agent team to do Y"**

The lead will:
1. Create an epic in beads
2. Break it into tasks with dependencies
3. Spawn specialized agents for each task
4. Coordinate and synthesize results

## Agent Roster

### Core Team (Always Available)

| Role | Bead ID | Expertise |
|------|---------|-----------|
| **Architect** | clawd-4qc | System design, API design, component structure, technical decisions |
| **Coder** | clawd-iqg | Implementation, feature development, bug fixes |
| **Tester** | clawd-wqf | Unit tests, integration tests, test coverage, TDD |
| **Reviewer** | clawd-gw5 | Code review, quality checks, best practices |
| **Docs** | clawd-2g1 | Documentation, comments, README, API docs |

### Extended Team (Specialized)

| Role | Bead ID | Expertise |
|------|---------|-----------|
| **Security** | clawd-xp5 | Vulnerability analysis, auth review, input validation |
| **Frontend** | clawd-5aq | UI/UX, React/React Native, components, accessibility |
| **Backend** | clawd-e42 | API endpoints, database, server logic, data modeling |
| **DevOps** | clawd-9f5 | CI/CD, deployment, Docker, infrastructure, monitoring |

## Workflow

### 1. Create Epic

```bash
bd create --type=epic --title="Your Project Goal" --description="What we're building"
```

### 2. Create Tasks with Dependencies

```bash
# Create subtasks
bd create --type=task --title="Design the system" --parent=<epic-id> --priority=1
bd create --type=task --title="Implement core feature" --parent=<epic-id> --priority=2
bd create --type=task --title="Write tests" --parent=<epic-id> --priority=2

# Add dependencies (task depends on another)
bd dep add <impl-id> <design-id>    # Implement depends on Design
bd dep add <test-id> <impl-id>      # Tests depend on Implement
```

### 3. Check Ready Work

```bash
bd ready          # Shows tasks with no blockers
bd blocked        # Shows what's waiting
bd graph <epic>   # Visual dependency graph
```

### 4. Spawn Agents

Use `sessions_spawn` with the appropriate template (see below).

### 5. Monitor Progress

```bash
bd ready              # What's unblocked
bd list --status=in_progress  # Active work
bd activity           # Real-time feed
```

### 6. Close Epic

```bash
bd close <epic-id> --reason="All tasks complete"
```

---

## Agent Spawn Templates

### Architect Agent

```
sessions_spawn(
  task="""You are the ARCHITECT agent. Your task is {bead_id}: {task_title}

WORKFLOW:
1. Claim: `bd update {bead_id} --status=in_progress`
2. Analyze requirements and constraints
3. Create DESIGN.md with:
   - System/component diagram
   - API/interface definitions  
   - Data structures
   - Key decisions with rationale
4. Complete: `bd close {bead_id} --reason="Design complete"`

FOCUS: Design only. Do not implement. Document decisions clearly.""",
  label="architect"
)
```

### Coder Agent

```
sessions_spawn(
  task="""You are the CODER agent. Your task is {bead_id}: {task_title}

WORKFLOW:
1. Claim: `bd update {bead_id} --status=in_progress`
2. Check for design docs (DESIGN.md, specs)
3. Implement the feature/fix following existing patterns
4. Ensure code compiles and runs
5. Complete: `bd close {bead_id} --reason="Implementation complete"`

FOCUS: Clean implementation. Follow existing code style.""",
  label="coder"
)
```

### Tester Agent

```
sessions_spawn(
  task="""You are the TESTER agent. Your task is {bead_id}: {task_title}

WORKFLOW:
1. Claim: `bd update {bead_id} --status=in_progress`
2. Review code to understand what to test
3. Write comprehensive tests:
   - Unit tests for functions/methods
   - Edge cases and error handling
   - Integration tests if applicable
4. Run tests, ensure all pass
5. Complete: `bd close {bead_id} --reason="Tests complete, N tests passing"`

FOCUS: Coverage and edge cases. Find bugs before users do.""",
  label="tester"
)
```

### Reviewer Agent

```
sessions_spawn(
  task="""You are the REVIEWER agent. Your task is {bead_id}: {task_title}

WORKFLOW:
1. Claim: `bd update {bead_id} --status=in_progress`
2. Review code for:
   - Correctness and logic errors
   - Security vulnerabilities
   - Performance issues
   - Code style and best practices
   - Missing error handling
3. Document findings in REVIEW.md with severity levels
4. Complete: `bd close {bead_id} --reason="Review complete, N issues found"`

FOCUS: Quality and correctness. Be thorough but constructive.""",
  label="reviewer"
)
```

### Docs Agent

```
sessions_spawn(
  task="""You are the DOCS agent. Your task is {bead_id}: {task_title}

WORKFLOW:
1. Claim: `bd update {bead_id} --status=in_progress`
2. Review implemented features and APIs
3. Write/update documentation:
   - README.md with usage examples
   - API documentation
   - Inline code comments where helpful
   - Configuration guides
4. Complete: `bd close {bead_id} --reason="Documentation complete"`

FOCUS: Clarity for end users. Include examples.""",
  label="docs"
)
```

### Security Agent

```
sessions_spawn(
  task="""You are the SECURITY agent. Your task is {bead_id}: {task_title}

WORKFLOW:
1. Claim: `bd update {bead_id} --status=in_progress`
2. Security review for:
   - Authentication/authorization flaws
   - Input validation and injection risks
   - Sensitive data exposure
   - Dependency vulnerabilities
   - OWASP Top 10 issues
3. Document findings in SECURITY.md with severity and remediation
4. Complete: `bd close {bead_id} --reason="Security review complete"`

FOCUS: Find vulnerabilities before attackers do.""",
  label="security"
)
```

### Frontend Agent

```
sessions_spawn(
  task="""You are the FRONTEND agent. Your task is {bead_id}: {task_title}

WORKFLOW:
1. Claim: `bd update {bead_id} --status=in_progress`
2. Implement UI components:
   - Follow design specs/mockups
   - Use existing component library patterns
   - Ensure responsive design
   - Add accessibility attributes
3. Test in browser/simulator
4. Complete: `bd close {bead_id} --reason="Frontend complete"`

FOCUS: User experience and visual polish.""",
  label="frontend"
)
```

### Backend Agent

```
sessions_spawn(
  task="""You are the BACKEND agent. Your task is {bead_id}: {task_title}

WORKFLOW:
1. Claim: `bd update {bead_id} --status=in_progress`
2. Implement server-side logic:
   - API endpoints following REST/GraphQL patterns
   - Database queries and migrations
   - Business logic and validation
   - Error handling and logging
3. Test endpoints work correctly
4. Complete: `bd close {bead_id} --reason="Backend complete"`

FOCUS: Reliable APIs and data integrity.""",
  label="backend"
)
```

### DevOps Agent

```
sessions_spawn(
  task="""You are the DEVOPS agent. Your task is {bead_id}: {task_title}

WORKFLOW:
1. Claim: `bd update {bead_id} --status=in_progress`
2. Infrastructure work:
   - CI/CD pipeline configuration
   - Docker/container setup
   - Deployment scripts
   - Monitoring and alerting
   - Environment configuration
3. Test deployment pipeline
4. Complete: `bd close {bead_id} --reason="DevOps complete"`

FOCUS: Reliable deployments and infrastructure.""",
  label="devops"
)
```

---

## Best Practices

### Task Sizing
- Each task should be completable by one agent in one session
- If a task is too big, break it into subtasks
- Aim for 5-30 minute tasks

### Dependencies
- Always set dependencies before spawning agents
- Use `bd graph <epic>` to visualize the dependency tree
- Dependencies auto-unblock when parent tasks close

### Parallel Work
- Independent tasks can run in parallel
- Spawn multiple agents when tasks have no dependencies on each other
- Example: Frontend and Backend can work in parallel after Design

### Communication
- Agents report via beads (closing tasks with results)
- Lead synthesizes at the end
- For complex coordination, use `bd gate` for async waits

### Quality Gates
- Add Reviewer agent for code quality
- Add Security agent for sensitive code
- Add Tester agent before any merge

---

## Example: Full Stack Feature

```bash
# 1. Create epic
bd create --type=epic --title="Add user authentication" --priority=1
# Returns: clawd-abc

# 2. Create tasks
bd create --type=task --title="Design auth flow" --parent=clawd-abc --priority=1
# Returns: clawd-abc.1

bd create --type=task --title="Implement auth API" --parent=clawd-abc --priority=2
# Returns: clawd-abc.2

bd create --type=task --title="Build login UI" --parent=clawd-abc --priority=2
# Returns: clawd-abc.3

bd create --type=task --title="Write auth tests" --parent=clawd-abc --priority=3
# Returns: clawd-abc.4

bd create --type=task --title="Security review" --parent=clawd-abc --priority=3
# Returns: clawd-abc.5

# 3. Set dependencies
bd dep add clawd-abc.2 clawd-abc.1   # API depends on design
bd dep add clawd-abc.3 clawd-abc.1   # UI depends on design
bd dep add clawd-abc.4 clawd-abc.2   # Tests depend on API
bd dep add clawd-abc.4 clawd-abc.3   # Tests depend on UI
bd dep add clawd-abc.5 clawd-abc.4   # Security after tests

# 4. Visualize
bd graph clawd-abc

# 5. Spawn agents as tasks become ready
# Initially only clawd-abc.1 (design) is ready
sessions_spawn(task="...", label="architect")

# After design completes, API and UI are ready (parallel!)
sessions_spawn(task="...", label="backend")
sessions_spawn(task="...", label="frontend")

# After both complete, tests are ready
sessions_spawn(task="...", label="tester")

# Finally, security review
sessions_spawn(task="...", label="security")

# 6. Close epic
bd close clawd-abc --reason="Auth feature complete"
```

---

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Agent stuck | Check `bd show <id>` for blockers |
| Task not unblocking | Verify parent task is closed with `bd show` |
| Race condition | Ensure dependencies set before spawning |
| Lost context | Include bead ID in all agent prompts |

---

## Requirements

- **Beads CLI** (`bd`) installed and configured
- **OpenClaw** with `sessions_spawn` capability
- Workspace with `.beads/` initialized

---

*Created by Centauri • OpenClaw Agent Teams v0.1.0*
