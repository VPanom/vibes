# Contributing to Vibes

Thank you for your interest in contributing! This guide covers how to add and modify components in this repository.

## Design Philosophy

This repository follows these core principles:

1. **Modularity** - Each component (skills, agents, templates) is self-contained and reusable
2. **Documentation-First** - Every component has comprehensive documentation
3. **Progressive Complexity** - Start simple, add complexity only when needed
4. **Real-World Focus** - Patterns and practices drawn from production experience
5. **Interoperability** - Components work together and with external tools

## Component Relationships

### How Components Work Together

**Skills** teach Claude how to work according to specific standards:
- Reference templates for consistent output format
- Can trigger agent workflows for complex tasks
- Compose with other skills automatically
- Work across Claude.ai, Claude Code, and API

**Agents** orchestrate workflows using skills:
- Combine multiple skills for consistent behavior
- Follow patterns documented in best practices
- Can be composed into more complex agents
- Implement decision-making and tool use

**Templates** provide structured starting points:
- Referenced by spec-generation skills
- Guide agent behavior when creating specifications
- Ensure consistency across projects
- Can be customized per organization

## Adding Skills

### Skill Structure

```
skills/category/skill-name/
├── SKILL.md              # Required: Main instruction file
├── examples/             # Optional: Usage examples
│   └── example-1.md
├── resources/            # Optional: Reference materials
│   └── reference.md
└── LICENSE.txt           # Optional: If different from repo
```

### SKILL.md Format

```markdown
---
name: skill-name
description: Brief description of what this skill does
license: MIT
---

## When to use this skill

Describe specific scenarios where Claude should apply this skill.
Be clear about the context and triggers.

## How to use this skill

Provide step-by-step instructions that Claude can follow:

1. **Step one**
   - Detailed sub-steps
   - What to check for

2. **Step two**
   - Clear actions to take
   - Expected outcomes

3. **Step three**
   - Final deliverables
   - Validation steps

## Keywords

trigger words, activation phrases, relevant terms, use cases
```

### Best Practices for Skills

**Instructions:**
- Write clear, specific, actionable steps
- Use imperative language ("Check for...", "Verify that...")
- Include examples of good and bad outputs
- Document edge cases and error handling

**Keywords:**
- Use natural language that users would actually type
- Include variations and synonyms
- Test that keywords trigger the skill appropriately

**Testing:**
- Test with various inputs to ensure reliability
- Verify the skill composes well with other skills
- Check that templates are referenced correctly
- Validate output against examples

**Documentation:**
- Update the category README.md when adding a skill
- Include real-world usage examples
- Document dependencies on other skills or templates
- Note any limitations or known issues

## Adding Agents

### Agent Categories

**workflows/** - Predefined patterns:
- Prompt chaining
- Routing and classification
- Parallelization
- Orchestrator-workers

**autonomous/** - Autonomous implementations:
- Tool use and decision making
- Dynamic task breakdown
- Self-validation and error recovery
- Long-running workflows

### Agent Structure

```
agents/category/agent-name/
├── README.md             # Overview and usage
├── implementation.*      # Code/config
├── config.json           # Optional: Configuration
└── examples/             # Usage examples
    └── example-1.md
```

### Agent Documentation Requirements

**README.md should include:**
- Clear description of what the agent does
- When to use this pattern vs others
- Step-by-step workflow explanation
- Example inputs and outputs
- Error handling approach
- Testing guidance
- Skills used or required

**Best Practices:**
- Start with simple patterns before complex ones
- Implement clear stopping conditions
- Add comprehensive logging and monitoring
- Test in sandboxed environments
- Document decision-making process
- Include error recovery mechanisms

## Adding Templates

### Template Structure

```
templates/category/
├── README.md             # Usage guide
└── template-name.md      # The template
```

### Template Format

```markdown
# [Template Title]

**Version:** 1.0
**Last Updated:** YYYY-MM-DD
**Status:** Draft | Review | Approved

## Overview
[Brief description of what this template is for]

## Section One
[Guidance for this section]

### Subsection
[More specific guidance]

## Section Two
[Continue with clear structure]

---
**Instructions:**
- Delete instruction sections before publishing
- Fill in [bracketed] placeholders
- Adjust sections as needed for your use case
```

### Template Best Practices

- Include all standard sections for the spec type
- Provide inline guidance that can be deleted
- Use clear placeholders like [Project Name]
- Add examples where helpful
- Keep consistent formatting
- Version your templates
- Document changes in template header

### Creating Skills for Templates

Consider creating a skill that uses your template:

```markdown
---
name: use-my-template
description: Generate [type] specifications using my-template
---

## When to use this skill
When user asks to create a [spec type]...

## How to use this skill
1. Load the template from templates/category/template-name.md
2. Fill in sections based on user's requirements
3. Follow the template's inline guidance
...
```

## Versioning

### Skills
Use semantic versioning in SKILL.md header:
- **Major** (1.0.0 → 2.0.0): Breaking changes to instructions or output format
- **Minor** (1.0.0 → 1.1.0): New features or significant additions
- **Patch** (1.0.0 → 1.0.1): Bug fixes, clarifications, small improvements

### Templates
Include version in template header:
- Maintain change log in template file
- Preserve backward compatibility when possible
- Provide migration guides for breaking changes

### Agents
Version in implementation file or README:
- Document workflow changes
- Note skill dependencies and versions
- Track pattern evolution

## Testing

### Skills Testing
- Test with varied inputs (happy path and edge cases)
- Verify template usage is correct
- Check keyword triggering works as expected
- Validate composition with other skills
- Test in all platforms (Claude.ai, Claude Code, API)

### Agent Testing
- Unit test individual components
- Integration test full workflows
- Test error handling and recovery
- Performance benchmarking for complex agents
- Validate stopping conditions work

### Template Testing
- Use in real projects
- Validate completeness of sections
- Check clarity of guidance
- Test with skills that reference it
- Get feedback from actual users

## Documentation Standards

### Writing Style
- Use clear, professional language
- Be concise but comprehensive
- Include concrete examples
- Document edge cases and limitations
- Cross-reference related components

### Markdown Formatting
- Use proper heading hierarchy (# → ## → ###)
- Code blocks with language tags: ```bash, ```python, etc.
- Tables for comparison or reference data
- Lists for steps or items
- Bold for emphasis on **important** points

### README Updates
When adding a component:
1. Update the relevant category README.md
2. Add entry to the main README if it's a major addition
3. Update cross-references in related documentation
4. Maintain alphabetical or logical ordering

## Submission Guidelines

### Before Submitting
- [ ] Component follows established patterns
- [ ] Documentation is comprehensive
- [ ] Testing is complete
- [ ] Examples are included
- [ ] README files are updated
- [ ] Code/content is formatted consistently
- [ ] No sensitive information included

### Pull Request Format
**Title:** Brief, descriptive summary (e.g., "Add prompt-chaining agent pattern")

**Description should include:**
- What this adds/changes and why
- What problem it solves or use case it addresses
- Testing performed
- Any breaking changes or migration needed
- Related issues or discussions

### Review Process
- Maintainers will review for consistency with repo patterns
- May request changes or clarifications
- Once approved, will be merged and documented

## Modifying Existing Components

### Before Making Changes
1. Check for components that depend on this one
2. Assess impact of changes (breaking vs non-breaking)
3. Plan migration path if needed
4. Document all changes

### Making Changes
1. Maintain backward compatibility when possible
2. Increment version appropriately
3. Update all related documentation
4. Add migration guidance for breaking changes
5. Test affected components

### Deprecation Process
If removing or significantly changing a component:
1. Mark as deprecated in documentation
2. Provide migration path to replacement
3. Allow reasonable transition period
4. Update all references to point to new version

## Getting Help

- Review existing components for patterns
- Check [Anthropic's Building Effective Agents](https://www.anthropic.com/research/building-effective-agents)
- Read [Claude Skills Documentation](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview)
- Open an issue for questions or discussions

## Code of Conduct

- Be respectful and professional
- Provide constructive feedback
- Focus on improving the repository
- Help others learn and contribute
- Follow established patterns and guidelines

Thank you for contributing to Vibes!
