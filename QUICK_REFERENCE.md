# Quick Reference

Fast access to common tasks and patterns.

## Common Tasks

### Using a Skill

**In Claude.ai:**
```
Settings > Capabilities > Add Skill > Upload folder
```

**In Claude Code:**
```bash
# Place in project root
mkdir -p .claude/skills
cp -r /path/to/skill .claude/skills/
```

**Via API:**
Include skill content in system prompt or use Skills API.

### Creating a Specification

**Quick method:**
```
Ask Claude: "Create a spec for [feature/project/API]"
The spec-generator skill will automatically apply.
```

**Using template directly:**
```
1. Copy template from templates/
2. Fill in sections
3. Use as reference for implementation
```

### Building an Agent

**Start with pattern:**
```
1. Choose pattern from agents/workflows/
2. Copy implementation template
3. Customize for your use case
4. Test with examples
5. Add error handling
```

**Autonomous agent:**
```
1. Review agents/autonomous/ examples
2. Define clear stopping conditions
3. Implement comprehensive logging
4. Test in sandbox environment
```

## File Locations

### Skills
```
skills/
├── spec-templates/     # Specification generation
├── agents/            # Agent orchestration
├── prompt-engineering/ # Advanced prompting
└── examples/          # Reference skills
```

### Templates
```
templates/
├── project-specs/     # PRDs, feature specs
├── api-specs/         # API contracts
└── architecture-specs/ # ADRs, system design
```

### Agents
```
agents/
├── workflows/         # Predefined patterns
└── autonomous/        # Autonomous agents
```

### Documentation
```
docs/
└── best-practices/    # Guidelines and patterns
```

## Quick Commands

### Repository Navigation
```bash
# View structure
tree -L 2 -I '.git'

# Find skills
ls -la skills/*/

# Find templates
ls -la templates/*/

# View specific skill
cat skills/spec-templates/spec-generator/SKILL.md
```

### Working with Skills

**Create new skill:**
```bash
mkdir -p skills/category/my-skill/{examples,resources}
touch skills/category/my-skill/SKILL.md
```

**Test skill:**
```
Upload to Claude and try various queries that should trigger it
```

### Working with Templates

**Copy template:**
```bash
cp templates/project-specs/template.md my-project/spec.md
```

**Fill template with Claude:**
```
"Use the [template-name] template to create a spec for [project]"
```

### Working with Agents

**Copy pattern:**
```bash
cp -r agents/workflows/pattern-name my-project/
```

## Common Patterns

### Spec-Driven Development
```
1. Create spec: "Generate a PRD for user authentication"
2. Review and refine spec
3. Implement: "Build this following the spec"
4. Validate: "Review code against spec"
```

### Agent Workflow
```
1. Define task clearly
2. Let agent compose relevant skills
3. Agent orchestrates skill application
4. Monitor execution
5. Review results
```

### Skill Composition
```
Multiple skills apply automatically:
- Spec-generator creates structure
- Domain-specific skill adds details
- Validation skill checks completeness
```

## Skill Keywords

### Spec Generation
```
create spec, generate specification, write requirements, 
PRD, API spec, architecture decision, feature spec
```

### Code Review
```
review code, check code, code review, pr review
```

### Documentation
```
write docs, document this, create documentation
```

## Template Formats

### SKILL.md Header
```markdown
---
name: skill-name
description: Brief description
license: MIT
---
```

### Template Header
```markdown
# [Title]

**Version:** X.Y
**Author:** Name
**Date:** YYYY-MM-DD
**Status:** Draft | Review | Approved
```

## Error Handling

### Skill Not Triggering
```
1. Check keywords in query
2. Verify SKILL.md format
3. Try explicit mention: "Use [skill-name] to..."
```

### Agent Getting Stuck
```
1. Add iteration limits
2. Implement stopping conditions
3. Review skill instructions
4. Simplify workflow
```

## Best Practices Checklist

### Before Creating Skill
- [ ] Check if similar skill exists
- [ ] Define clear scope
- [ ] List example scenarios
- [ ] Plan resource needs

### Before Creating Agent
- [ ] Try simpler approach first
- [ ] Define success criteria
- [ ] Plan error handling
- [ ] Set up monitoring

### Before Using in Production
- [ ] Test thoroughly
- [ ] Document usage
- [ ] Set up monitoring
- [ ] Plan rollback

## Resource Links

### Documentation
- [Getting Started](./GETTING_STARTED.md)
- [Architecture](./ARCHITECTURE.md)
- [Main README](./README.md)

### Section READMEs
- [Skills](./skills/README.md)
- [Agents](./agents/README.md)
- [Templates](./templates/README.md)
- [Best Practices](./docs/best-practices/README.md)

### External Resources
- [Anthropic Docs](https://docs.anthropic.com/)
- [Building Effective Agents](https://www.anthropic.com/research/building-effective-agents)
- [Claude Skills](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview)

## Getting Help

### In This Repository
1. Check relevant README files
2. Review examples in each section
3. Consult best practices docs

### External Resources
1. Official Anthropic documentation
2. Claude API reference
3. Skills documentation
4. Community examples

## Version Information

### Repository Version
Check main README.md for current version

### Component Versions
- Skills: See individual SKILL.md files
- Templates: Check template header
- Agents: See implementation files

## Quick Troubleshooting

| Issue | Quick Fix |
|-------|-----------|
| Skill not working | Check SKILL.md format, verify keywords |
| Template incomplete | Compare with template in repo |
| Agent looping | Add stopping conditions, check logs |
| Unclear instructions | Add examples, be more specific |
| Slow performance | Profile, optimize context, use caching |

## Common File Patterns

### Skill Structure
```
skill-name/
├── SKILL.md
├── examples/
│   └── example-1.md
├── resources/
│   └── reference.md
└── LICENSE.txt
```

### Template Structure
```
template.md
- Header with metadata
- Section structure
- Inline guidance
- Examples
```

### Agent Structure
```
agent-name/
├── README.md
├── implementation.py
├── config.json
└── tests/
```
