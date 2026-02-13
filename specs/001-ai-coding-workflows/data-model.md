# Data Model: Workflow Documentation

**Date**: 2026-02-12  
**Purpose**: Define entities and relationships for documenting AI-assisted coding workflows.

## Entities

### Workflow

Represents a documented approach to AI-assisted coding.

**Attributes**:
- `name`: String - Display name (e.g., "Spec-Driven Development")
- `id`: String - URL-safe identifier (e.g., "spec-driven")
- `category`: Enum - One of: specification, skills, agents, hybrid
- `description`: String - One-sentence summary
- `target_users`: List<String> - Who should use this (e.g., "developers building new features")
- `estimated_adoption_time`: Integer - Minutes to adopt in existing project
- `platforms`: List<Platform> - Where it works (claude-code, claude-ai, api, all)

**Relationships**:
- Has many `Component`
- Has many `WorkflowStep`
- Has one `AdoptionGuide`
- Has many `Example`

**Validation Rules**:
- `name` must be unique across workflows
- `description` must be ≤100 characters (scannable)
- `estimated_adoption_time` must be ≤60 minutes (SC-002)

---

### Component

Represents a directory, file, script, or template that makes up a workflow.

**Attributes**:
- `type`: Enum - One of: directory, file, script, template, command
- `path`: String - Relative to repo root (e.g., ".specify/templates/spec-template.md")
- `purpose`: String - What this component does
- `required`: Boolean - Must have to use workflow
- `size_kb`: Integer - File/directory size (for adoption complexity assessment)

**Relationships**:
- Belongs to `Workflow`

**Validation Rules**:
- `path` must exist in repository
- `purpose` must be token-efficient (≤50 characters)

---

### WorkflowStep

Represents a single step in using a workflow.

**Attributes**:
- `order`: Integer - Sequence number (1, 2, 3...)
- `action`: String - What user does (imperative: "Create spec", "Run command")
- `command`: String (optional) - CLI command if applicable (e.g., "/speckit.specify")
- `expected_outcome`: String - What happens after this step
- `duration_estimate`: Integer - Minutes for this step
- `platform`: Enum - Where this step applies (all, claude-code, claude-ai, api)

**Relationships**:
- Belongs to `Workflow`

**Validation Rules**:
- Steps for same workflow must have sequential `order` (no gaps)
- `action` must start with verb (Create, Run, Copy, Configure, etc.)
- Total `duration_estimate` for workflow must align with `estimated_adoption_time`

---

### AdoptionGuide

Quick-start guide for integrating a workflow into a project.

**Attributes**:
- `prerequisites`: List<String> - What user needs (e.g., "Git", "Claude Code CLI")
- `estimated_time`: Integer - Minutes to complete adoption
- `copy_commands`: List<String> - Shell commands to copy files
- `config_steps`: List<String> - Manual configuration needed
- `test_command`: String - How to verify workflow works
- `test_expected`: String - What successful test looks like

**Relationships**:
- Belongs to one `Workflow`

**Validation Rules**:
- `estimated_time` must match workflow's `estimated_adoption_time`
- `copy_commands` must reference existing `Component` paths
- `test_command` should complete in <2 minutes (quick validation)

---

### Example

Working demonstration of a workflow in action.

**Attributes**:
- `name`: String - Example name (e.g., "spec-driven-example")
- `directory`: String - Path to example files (e.g., "docs/examples/spec-driven-example/")
- `demonstrates`: List<String> - Capabilities shown (e.g., "user story creation", "constitution check")
- `readme_path`: String - Path to example README explaining it
- `runnable`: Boolean - Can user execute this example directly?

**Relationships**:
- Belongs to `Workflow`
- References many `Component` (which components it uses)

**Validation Rules**:
- `directory` must exist and contain files
- Must have README explaining how to use example
- If `runnable=true`, README must include execution instructions

---

### Platform

Enum representing Claude platforms.

**Values**:
- `claude-code` - Claude Code CLI
- `claude-ai` - Claude.ai web interface  
- `api` - Anthropic API with tool use
- `all` - Works on all platforms

---

## Relationships Diagram

```
Workflow (1) ──< (many) Component
    │
    ├──< (many) WorkflowStep
    │
    ├──── (1) AdoptionGuide
    │
    └──< (many) Example ──< (many) Component
```

---

## State Transitions

### Workflow Status

```
draft → documented → validated → published
```

- **draft**: Initial state, documentation incomplete
- **documented**: All components, steps, guide complete
- **validated**: Adoption tested in real project, <30 min confirmed
- **published**: Added to repository README, discoverable

---

## Concrete Instances (from research.md)

### Workflow: Spec-Driven Development

```yaml
name: "Spec-Driven Development"
id: "spec-driven"
category: specification
description: "Feature planning through user stories, constitution checks, and task breakdown"
target_users: ["developers building new features", "teams needing governance"]
estimated_adoption_time: 20
platforms: [claude-code, all]

components:
  - type: directory
    path: ".specify/"
    purpose: "Specification system templates and scripts"
    required: true
  - type: template
    path: ".specify/templates/spec-template.md"
    purpose: "User story and requirements template"
    required: true
  - type: file
    path: ".specify/memory/constitution.md"
    purpose: "Project governance and principles"
    required: true

steps:
  - order: 1
    action: "Create specification"
    command: "/speckit.specify"
    expected_outcome: "spec.md with user stories generated"
    duration_estimate: 5
    platform: claude-code
  - order: 2
    action: "Generate plan"
    command: "/speckit.plan"
    expected_outcome: "plan.md with technical context and structure"
    duration_estimate: 10
    platform: claude-code
```

### Workflow: Skills-Based

```yaml
name: "Skills-Based Development"
id: "skills-based"
category: skills
description: "Reusable AI instructions for consistent behavior across platforms"
target_users: ["developers wanting portable AI patterns", "teams standardizing Claude usage"]
estimated_adoption_time: 5
platforms: [all]

components:
  - type: directory
    path: "skills/"
    purpose: "Skill library organized by category"
    required: false
  - type: file
    path: "skills/*/SKILL.md"
    purpose: "Individual Skill definition"
    required: true
```

### Workflow: Agent Patterns

```yaml
name: "Agent Patterns"
id: "agent-patterns"
category: agents
description: "Approval-based automation for repository maintenance"
target_users: ["developers automating repetitive tasks", "teams enforcing patterns"]
estimated_adoption_time: 15
platforms: [claude-code, api]

components:
  - type: file
    path: "agent.md"
    purpose: "Agent configuration and workflows"
    required: true
  - type: directory
    path: "agents/"
    purpose: "Agent pattern examples"
    required: false
```

---

## Documentation Content Model

Each workflow guide (`docs/workflows/*.md`) should contain:

1. **Overview** (≤3 sentences)
2. **When to Use** (bulleted use cases)
3. **Components** (what makes up this workflow)
4. **Steps** (sequential workflow execution)
5. **Adoption** (link to quick-start guide)
6. **Examples** (link to working examples)
7. **Integration** (how this combines with other workflows)

Target length: 200-300 lines (token-efficient per Constitution III).
