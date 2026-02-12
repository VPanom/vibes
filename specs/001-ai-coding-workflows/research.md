# Research: AI-Assisted Coding Workflows

**Date**: 2026-02-12  
**Purpose**: Analyze existing workflows in the Vibes repository to document their components, steps, and adoption requirements.

## Workflow 1: Spec-Driven Development

### Components

**Location**: `.specify/` directory

- `.specify/templates/` - Specification templates (spec, plan, tasks, checklist, agent-file, constitution)
- `.specify/scripts/bash/` - Automation scripts (create-new-feature.sh, setup-plan.sh, update-agent-context.sh)
- `.specify/memory/` - Project governance (constitution.md)
- `.opencode/command/` - CLI commands (speckit.specify.md, speckit.plan.md)

### Workflow Steps

1. **Create Specification**: `/speckit.specify "feature description"`
   - Creates branch `###-feature-name`
   - Generates `specs/###-feature-name/spec.md` with user stories
   - Validates against quality checklist
   - Resolves [NEEDS CLARIFICATION] markers (max 3)

2. **Generate Plan**: `/speckit.plan`
   - Analyzes spec and asks technical context questions
   - Creates `plan.md` with constitution check, structure, complexity tracking
   - Phase 0: Generates `research.md` (resolves unknowns)
   - Phase 1: Creates `data-model.md`, `contracts/`, `quickstart.md`

3. **Break Down Tasks**: `/speckit.tasks`
   - Reads spec user stories and plan structure
   - Generates `tasks.md` organized by user story (P1, P2, P3)
   - Enables incremental, independent implementation

### Adoption Requirements

**Prerequisites**:
- Git repository
- Claude Code CLI (for `/speckit.*` commands) OR manual template usage

**Setup Steps**:
1. Copy `.specify/` directory to project root
2. Customize `.specify/memory/constitution.md` for project principles
3. Optionally install `.opencode/command/*.md` files for CLI commands

**Best Practices**:
- Start with constitution - defines project governance
- Use spec template strictly - AI agents parse it
- Keep [NEEDS CLARIFICATION] markers ≤3 - make informed guesses
- Organize tasks by user story - enables incremental delivery

### Use Cases

- Building new features with clear specifications
- Ensuring constitution compliance throughout development
- Breaking complex features into independently deliverable user stories
- Maintaining documentation-driven development discipline

---

## Workflow 2: Skills-Based Development

### Components

**Location**: `/skills/` directory

- `skills/spec-templates/` - Skills for generating specifications
- `skills/prompt-engineering/` - Advanced prompting techniques (conventional-commits)
- `skills/agents/` - Agent-related Skills
- `skills/examples/` - Example Skills
- Each Skill has: `SKILL.md`, `examples/`, optional `resources/`

### Workflow Steps

1. **Discover Skill**: Browse `/skills/` by category or search README
   - Categories: spec-templates, prompt-engineering, agents, examples
   - Each category README lists available Skills

2. **Load Skill**: Reference in Claude conversation
   - Claude Code: Skills auto-load from project
   - Claude.ai: Copy SKILL.md content or reference by name
   - API: Include Skill instructions in system prompt

3. **Use Skill**: Invoke based on activation context
   - Skills activate when keywords/context match
   - Example: "conventional-commits" skill triggers on commit message requests

### Adoption Requirements

**Prerequisites**:
- Access to Claude platform (Code, Web, or API)
- Basic understanding of Markdown

**Setup Steps**:
1. Browse `skills/` to find relevant Skills
2. Copy desired Skill directory to your project (optional)
3. Reference Skill in Claude conversations

**Best Practices**:
- Skills are self-contained - copy individual Skills, not entire directory
- Check SKILL.md for activation keywords and usage examples
- Skills should follow constitution (token-efficient, cross-platform)

### Skill Structure

```
skill-name/
├── SKILL.md           # Required: name, description, when/how to use, keywords
├── examples/          # Recommended: working examples
│   └── examples.md
└── resources/         # Optional: templates, reference files
```

### Use Cases

- Reusing AI instructions across projects
- Standardizing AI behavior (e.g., commit message format)
- Teaching Claude project-specific patterns
- Building library of proven AI prompts

---

## Workflow 3: Agent Patterns

### Components

**Location**: `/agents/` and `agent.md`

- `/agents/autonomous/repo-agent/` - Repository maintenance agent with approval workflow
- `/agents/workflows/` - Predefined agent workflow patterns (currently empty)
- `agent.md` - Agent configuration and behavior rules (root level)

### Workflow Steps

**Autonomous Agent Pattern** (from `agent.md`):

1. **Define Agent Purpose**: Configure agent behavior in agent.md
   - Core principles (human-in-loop, never touch git, follow patterns, stay concise)
   - Workflows (add skill, add template, validate, update docs, generate examples)
   - Validation rules and approval points

2. **Invoke Agent Workflow**: Trigger specific workflow
   - "Add a skill for [topic]" → Skill creation workflow
   - "Validate [path]" → Validation workflow
   - "Update docs" → Documentation sync workflow

3. **Human Approval Loop**: Agent shows preview, waits for approval
   - Agent generates content → shows preview → waits
   - User approves/rejects/requests edits
   - Agent executes only after approval

4. **Execute with Safeguards**: Agent performs approved actions
   - Never git operations unless explicitly instructed
   - Never delete without confirmation
   - Stop and ask when uncertain

### Adoption Requirements

**Prerequisites**:
- Claude Code or API access with tool use
- Repository with defined structure

**Setup Steps**:
1. Copy `agent.md` to project root
2. Customize agent workflows for project needs
3. Define agent stopping conditions and approval points

**Best Practices**:
- Always require human approval before file operations
- Define clear workflows with explicit steps
- Set stopping conditions (validation fails, conflicts, uncertainty)
- Keep agent output concise (constitution principle III)

### Use Cases

- Automating repetitive repository maintenance
- Scaffolding new Skills/templates with validation
- Keeping documentation in sync with code changes
- Enforcing repository patterns and conventions

---

## Decision Matrix: Which Workflow When?

| Use Case | Recommended Workflow | Why |
|----------|---------------------|-----|
| Building new feature | Spec-Driven | Ensures requirements clarity, constitution compliance, incremental delivery |
| Reusing AI instructions | Skills-Based | Portable, self-contained, platform-agnostic |
| Automating repo tasks | Agent Patterns | Approval-based automation with safeguards |
| Onboarding new project | Spec-Driven | Constitution establishes governance from day 1 |
| Standardizing AI behavior | Skills-Based | Skills work across all Claude platforms |
| Repository maintenance | Agent Patterns | Reduces manual work while maintaining control |

---

## Cross-Workflow Integration

These workflows complement each other:

- **Spec-Driven + Skills**: Use Skills during spec generation for consistent formatting
- **Spec-Driven + Agent**: Agent validates specs against constitution, generates boilerplate
- **Skills + Agent**: Agent creates new Skills following validated patterns

**Example Combined Workflow**:
1. Use Spec-Driven to plan feature (`/speckit.specify`, `/speckit.plan`)
2. Use Skills during implementation (conventional-commits, prompt patterns)
3. Use Agent to maintain documentation (update READMEs, validate structure)

---

## Adoption Time Estimates

Based on repository structure and documentation completeness:

- **Spec-Driven**: ~20 min (copy `.specify/`, customize constitution)
- **Skills-Based**: ~5 min per Skill (copy Skill directory, reference in Claude)
- **Agent Patterns**: ~15 min (copy agent.md, customize workflows)

All estimates assume user familiar with Git and basic Claude usage.
