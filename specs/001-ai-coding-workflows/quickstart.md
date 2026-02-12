# Quick-Start Template Structure

**Date**: 2026-02-12  
**Purpose**: Define the standard structure for all workflow quick-start guides.

## Template Format

Each quick-start guide follows this structure for consistency and token efficiency:

```markdown
# Quick Start: [Workflow Name]

**Time**: ~[X] minutes | **Prerequisites**: [comma-separated list]

## Copy to Your Project

​```bash
# Single command to copy necessary files
[copy command]
​```

## Configure

[2-3 numbered configuration steps, each ≤1 sentence]

## Test It

​```bash
# Simple test command
[command]
​```

**Expected**: [one sentence describing successful outcome]

## Next Steps

- Read full guide: [link]
- See example: [link]
```

---

## Design Principles

### Token Efficiency (Constitution III)
- Total length: 30-50 lines (scannable in <1 min)
- No explanatory prose - commands and expected outcomes only
- Bullet points and code blocks over paragraphs

### Quick Success (SC-002)
- User completes guide in ≤30 minutes
- Test command runs in <2 minutes
- Immediate feedback on success/failure

### Platform Awareness
- If workflow works on all platforms: no platform qualifier
- If platform-specific: add note after Prerequisites

---

## Concrete Examples

### Quick Start: Spec-Driven Development

```markdown
# Quick Start: Spec-Driven Development

**Time**: ~20 minutes | **Prerequisites**: Git, Claude Code CLI

## Copy to Your Project

​```bash
cp -r /path/to/vibes/.specify ./
​```

## Configure

1. Edit `.specify/memory/constitution.md` - replace principles with your project's governance
2. Optional: Copy `.opencode/command/speckit.*.md` for CLI commands

## Test It

​```bash
/speckit.specify "Add user authentication"
​```

**Expected**: Branch `001-user-auth` created with `specs/001-user-auth/spec.md`

## Next Steps

- Read full guide: [docs/workflows/spec-driven.md](../../../docs/workflows/spec-driven.md)
- See example: [docs/examples/spec-driven-example/](../../../docs/examples/spec-driven-example/)
```

---

### Quick Start: Skills-Based Development

```markdown
# Quick Start: Skills-Based Development

**Time**: ~5 minutes | **Prerequisites**: Claude access (any platform)

## Copy to Your Project

​```bash
# Copy specific Skill (example: conventional-commits)
cp -r /path/to/vibes/skills/prompt-engineering/conventional-commits ./skills/
​```

## Configure

1. No configuration needed - Skills work out of the box
2. Optional: Create `skills/README.md` to document your Skill library

## Test It

Reference the Skill in Claude conversation:

​```
"Write a commit message for the changes in this PR"
​```

**Expected**: Commit message follows conventional commits format (if skill loaded)

## Next Steps

- Read full guide: [docs/workflows/skills-based.md](../../../docs/workflows/skills-based.md)
- Browse Skills: [skills/](../../../skills/)
- See example: [docs/examples/skills-example/](../../../docs/examples/skills-example/)
```

---

### Quick Start: Agent Patterns

```markdown
# Quick Start: Agent Patterns

**Time**: ~15 minutes | **Prerequisites**: Claude Code CLI with tool access

## Copy to Your Project

​```bash
cp /path/to/vibes/agent.md ./
​```

## Configure

1. Edit `agent.md` - customize workflows for your project's needs
2. Define agent stopping conditions (when to ask vs act)

## Test It

​```bash
# In Claude Code
"Validate the structure of my project"
​```

**Expected**: Agent runs validation checks and reports results (no files changed without approval)

## Next Steps

- Read full guide: [docs/workflows/agent-patterns.md](../../../docs/workflows/agent-patterns.md)
- See example: [docs/examples/agents-example/](../../../docs/examples/agents-example/)
- Agent reference: [agents/autonomous/repo-agent/](../../../agents/autonomous/repo-agent/)
```

---

## Validation Checklist

Before publishing any quick-start guide:

- [ ] Follows template structure exactly
- [ ] Total length ≤50 lines
- [ ] Copy command tested and works
- [ ] Test command completes in <2 minutes
- [ ] Expected outcome is specific and observable
- [ ] Links are valid (relative paths from guide location)
- [ ] No unexplained jargon or assumptions
- [ ] Time estimate matches actual adoption time

---

## Multi-Platform Variations

If workflow has platform-specific steps, use tabs/sections:

```markdown
## Copy to Your Project

**Claude Code / API**:
​```bash
cp -r /path/to/vibes/.specify ./
​```

**Claude.ai Web**:
1. Download `.specify/` directory from [repository link]
2. Reference templates in conversation context

[rest of guide assumes platform chosen]
```

---

## Maintenance

Quick-start guides must stay in sync with:
- Component paths (if files move)
- Command syntax (if CLI changes)
- Time estimates (if workflow simplified/complicated)
- Constitution principles (if governance updates)

Update trigger: Any change to referenced Components or WorkflowSteps.
