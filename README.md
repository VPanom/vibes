# Vibes

A curated collection of production-ready Claude Skills for building effective AI applications.

## Quick Start

**1. Clone or download this repository**

**2. Use a skill in Claude.ai:**
```
Settings > Capabilities > Add Skill > Upload folder
Select a skill folder (e.g., skills/prompt-engineering/conventional-commits/)
```

**3. Use a skill in Claude Code:**
```bash
# Copy skill to your project
cp -r /path/to/vibes/skills/spec-templates/spec-generator .claude/skills/
```

**4. Try it:**
```
"Create a spec for a user authentication system"
Claude will automatically apply the spec-generator skill
```

## What's Inside

### Skills (`skills/`)
Reusable capabilities that teach Claude how to work according to your standards and procedures.

- **spec-templates/** - Generate comprehensive specifications (PRDs, technical specs, ADRs)
- **prompt-engineering/** - Advanced prompting techniques (conventional commits, etc.)
- **examples/** - Community-contributed and reference skills

Each skill is a folder with a `SKILL.md` file containing instructions Claude automatically applies when relevant.

### Agents (`agents/`)
Practical implementations of agent patterns and workflows.

- **workflows/** - Predefined patterns (prompt chaining, routing, parallelization, orchestrator-workers)
- **autonomous/** - Autonomous agents with dynamic decision-making and tool access

### Templates (`templates/`)
Spec-driven development templates for consistent project documentation.

- **project-specs/** - Product requirement documents and feature specifications
- **api-specs/** - API design and contract templates
- **architecture-specs/** - Architecture decision records and system design docs

### Documentation (`docs/`)
Best practices and guides for building effective AI systems.

## Using Skills

### In Claude.ai
1. Navigate to Settings > Capabilities
2. Click "Add Skill" and upload the skill folder
3. Claude automatically applies it when relevant keywords appear in your conversation

### In Claude Code
```bash
# Place skills in your project root
mkdir -p .claude/skills
cp -r /path/to/skill .claude/skills/

# Claude Code detects and uses them automatically
```

### Via API
Include the skill's `SKILL.md` content in your system prompt or use the Skills API. See [Claude Skills Documentation](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) for details.

### Skill Structure
```
my-skill/
├── SKILL.md          # Main instruction file (required)
├── examples/         # Optional: example inputs/outputs
└── resources/        # Optional: reference files, templates
```

## Common Workflows

### Spec-Driven Development
```
1. Ask: "Create a spec for [feature/project/API]"
2. Claude uses spec-generator skill to create structured specification
3. Review and refine the spec
4. Ask: "Implement this following the spec"
5. Claude builds implementation adhering to specification
```

**Why it works:**
- Specifications provide clear requirements and success criteria
- Skills ensure consistent spec format across projects
- Implementation follows documented standards
- Easy to review and validate against spec

### Agent Patterns

**Prompt Chaining** - Break complex tasks into sequential steps
```
Good for: Document generation, data transformation, analysis
Pattern: Step 1 output → Step 2 input → Step 3 input → Final result
```

**Routing** - Classify input and direct to specialized handlers
```
Good for: Customer support, multi-domain systems
Pattern: Classifier → Route to specialist → Handle with domain skill
```

**Orchestrator-Workers** - Dynamic task breakdown and delegation
```
Good for: Complex coding tasks, research projects
Pattern: Orchestrator plans → Delegates to workers → Aggregates results
```

**Autonomous Agents** - LLM-driven decision making with tool access
```
Good for: Open-ended problems, extended workflows
Pattern: Observe → Decide → Act → Validate → Repeat until goal met
```

See `agents/workflows/` for implementation examples and detailed documentation.

### Skill Composition

Multiple skills can apply automatically to a single task:

```
User: "Create an API specification for user authentication"

Claude applies:
1. spec-generator skill (creates structure)
2. API spec template (provides format)
3. Security best practices skill (if available)

Result: Comprehensive, well-structured API spec
```

## Quick Reference

### Common Tasks

**Use an existing skill:**
```
Upload folder in Claude.ai or copy to .claude/skills/ in Claude Code
```

**Create a new skill:**
```bash
mkdir -p skills/category/my-skill
cat > skills/category/my-skill/SKILL.md <<'EOF'
---
name: skill-name
description: What this skill does
license: MIT
---

## When to use this skill
Describe scenarios where this applies

## How to use this skill
Step-by-step instructions

## Keywords
trigger, words, skill activation
EOF
```

**Generate a specification:**
```
"Create a [PRD/technical spec/ADR] for [topic]"
```

**Build following a spec:**
```
"Implement the authentication system following the spec"
```

### File Locations

```
vibes/
├── skills/
│   ├── spec-templates/spec-generator/    # Spec generation skill
│   ├── prompt-engineering/conventional-commits/  # Commit message skill
│   └── examples/                          # Reference skills
├── agents/
│   ├── workflows/                         # Agent patterns
│   └── autonomous/                        # Autonomous implementations
├── templates/
│   ├── project-specs/                     # PRD templates
│   ├── api-specs/                         # API templates
│   └── architecture-specs/                # ADR templates
└── docs/
    └── best-practices/                    # Guidelines
```

### Essential Commands

```bash
# View repository structure
tree -L 2 -I '.git'

# List all skills
ls -la skills/*/

# View a specific skill
cat skills/spec-templates/spec-generator/SKILL.md

# Copy template for use
cp templates/project-specs/template.md my-project/spec.md
```

### Keywords for Automatic Skill Triggering

**Spec generation:**
`create spec, generate specification, write requirements, PRD, API spec, architecture decision, feature spec`

**Code review:**
`review code, check code, code review, pr review, pull request review`

**Commit messages (conventional-commits skill):**
`create commit, commit message, conventional commit`

## Best Practices

### For Skills
- Write clear, specific instructions that Claude can follow consistently
- Include concrete examples of input/output
- Use descriptive keywords that match natural language queries
- Test with various inputs to ensure reliability
- Document edge cases and limitations

### For Specifications
- Be thorough but concise - include all necessary details without fluff
- Define clear acceptance criteria and success metrics
- Document constraints and dependencies upfront
- Version your specs and track changes
- Use templates for consistency across projects

### For Agents
- Start simple and add complexity only when needed
- Implement error handling and recovery mechanisms
- Set clear stopping conditions to prevent infinite loops
- Log decisions and actions for debugging
- Test in sandboxed environments before production use

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Skill not triggering automatically | Check that keywords in your query match skill's keyword list. Try explicitly mentioning: "Use the [skill-name] skill to..." |
| Agent stuck in loop | Add iteration limits and stopping conditions. Review agent instructions for clarity. |
| Inconsistent spec output | Ensure template is properly referenced in skill. Add more specific examples in SKILL.md. |
| Skill not found in Claude.ai | Verify folder structure includes SKILL.md with proper frontmatter. Re-upload the folder. |

## Going Deeper

### Section Documentation
Each major section has detailed documentation:
- [Skills README](./skills/README.md) - Comprehensive skills guide
- [Agents README](./agents/README.md) - Agent patterns and implementations
- [Templates README](./templates/README.md) - Template usage and customization
- [Best Practices](./docs/best-practices/README.md) - Collected wisdom

### External Resources
- [Anthropic Documentation](https://docs.anthropic.com/) - Official Claude documentation
- [Building Effective Agents](https://www.anthropic.com/research/building-effective-agents) - Anthropic's agent design guide
- [Claude Skills Documentation](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview) - Skills API reference

## Contributing

Contributions are welcome! See [CONTRIBUTING.md](./CONTRIBUTING.md) for guidelines on adding skills, agents, and templates.

## License

MIT License - See LICENSE file for details
