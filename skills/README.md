# Skills

This directory contains reusable Claude Skills that teach Claude how to perform tasks according to specific standards and procedures.

## What is a Skill?

A Skill is a folder containing a `SKILL.md` file with structured instructions. Claude automatically applies relevant Skills based on the task at hand, ensuring consistent and expert-level outputs.

## Structure

- **spec-templates/** - Skills for generating and working with specifications
- **agents/** - Skills for orchestrating agent behaviors and workflows
- **prompt-engineering/** - Advanced prompting techniques and patterns
- **examples/** - Reference Skills and community contributions

## Creating a Skill

### Basic Format

```
skill-name/
├── SKILL.md          # Required: Main instruction file
├── examples/         # Optional: Example inputs and outputs
├── resources/        # Optional: Reference files, templates
└── LICENSE.txt       # Optional: License information
```

### SKILL.md Template

```markdown
---
name: unique-skill-name
description: Clear description of what this skill does and when to use it
license: MIT (or your chosen license)
---

## When to use this skill
Describe the specific scenarios where Claude should apply this skill.

## How to use this skill

Provide step-by-step instructions:

1. **First step**
   - Detailed guidance
   - Expected behavior

2. **Second step**
   - More instructions
   - Edge cases to consider

## Keywords
keyword1, keyword2, related terms, trigger phrases
```

## Best Practices

### Writing Effective Instructions

1. **Be Specific**: Provide concrete steps rather than vague guidance
2. **Include Examples**: Show expected inputs and outputs
3. **Handle Edge Cases**: Document what to do when things don't fit the standard pattern
4. **Use Clear Language**: Write as if instructing a knowledgeable colleague
5. **Test Thoroughly**: Verify the skill works across different scenarios

### Organizing Resources

- Keep related files in the skill's folder
- Use descriptive filenames
- Document any external dependencies
- Include version information if relevant

### Naming Conventions

- Use lowercase with hyphens: `my-skill-name`
- Be descriptive but concise
- Avoid generic names that might conflict
- Consider namespacing for organization-specific skills

### Keywords

Keywords help Claude automatically detect when to use a skill:

- Include obvious trigger phrases
- Add domain-specific terminology
- Consider variations and synonyms
- Don't over-specify (let Claude use judgment)

## Skill Categories

### Spec Templates
Skills that help generate, validate, or work with specifications:
- Project requirement documents
- API contracts
- Architecture decision records
- Test specifications

### Agents
Skills that define agent behaviors and orchestration patterns:
- Multi-step workflows
- Decision trees
- Error recovery procedures
- Tool selection logic

### Prompt Engineering
Skills that embody advanced prompting techniques:
- Few-shot learning patterns
- Chain-of-thought reasoning
- Self-evaluation loops
- Context optimization

### Examples
Reference implementations demonstrating skill patterns:
- Production-tested skills
- Community contributions
- Tutorial skills
- Template skills

## Using Skills

### In Claude.ai
1. Navigate to Settings > Capabilities
2. Click "Add Skill"
3. Upload the skill folder
4. Claude will automatically apply when relevant

### In Claude Code
1. Place skills in `.claude/skills/` directory
2. Claude Code detects and loads automatically
3. Skills apply to all conversations and tasks

### Via API
Include skill content in system prompts or use the Skills API endpoint.

Reference: [Skills API Documentation](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview)

## Composing Skills

Claude can apply multiple skills simultaneously:

- Skills stack automatically when relevant
- More specific skills take precedence
- Instructions combine coherently
- No manual selection needed

Example: A task might trigger both a "code-review" skill and a "python-best-practices" skill simultaneously.

## Testing Skills

Before deploying a skill:

1. **Test basic scenarios** - Verify it works for common cases
2. **Test edge cases** - Check behavior with unusual inputs
3. **Test composition** - Ensure it works well with other skills
4. **Test keywords** - Verify automatic triggering works
5. **Get feedback** - Have others try the skill

## Contributing Skills

When contributing a skill to this repository:

1. Ensure it follows the standard format
2. Include comprehensive documentation
3. Add examples of usage
4. Test thoroughly
5. Document any limitations
6. Choose an appropriate license

## Troubleshooting

**Skill not being applied:**
- Check keywords match your query
- Verify SKILL.md format is correct
- Ensure description clearly defines scope
- Try explicitly mentioning the skill

**Conflicting skills:**
- Review which skills are active
- Make keywords more specific
- Adjust skill precedence in documentation
- Consider combining related skills

**Inconsistent results:**
- Add more concrete examples
- Make instructions more specific
- Test with varied inputs
- Refine edge case handling

## Examples

See the `examples/` directory for reference implementations covering:
- Document generation
- Code analysis
- Data transformation
- Research workflows
- Project management

## Resources

- [Claude Skills Documentation](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview)
- [Building Skills Blog Post](https://claude.com/blog/building-skills-for-claude-code)
- [Skills vs Other Approaches](https://claude.com/blog/skills-explained)
