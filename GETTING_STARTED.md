# Getting Started

This guide will help you understand and use the resources in this repository effectively.

## Prerequisites

- Access to Claude (via claude.ai, Claude Code, or API)
- Basic understanding of prompt engineering
- Familiarity with Claude's capabilities (tool use, artifacts, etc.)

## Quick Start

### 1. Understanding Skills

Skills are the foundation of this repository. A Skill is a folder containing a `SKILL.md` file that teaches Claude how to perform specific tasks according to your standards.

**Anatomy of a Skill:**
```
my-skill/
├── SKILL.md          # Main instruction file
├── examples/         # Optional: example inputs/outputs
└── resources/        # Optional: reference files, templates, etc.
```

**SKILL.md Format:**
```markdown
---
name: skill-name
description: Brief description of what this skill does
license: MIT
---

## When to use this skill
Describe the scenarios where Claude should apply this skill.

## How to use this skill
Step-by-step instructions for Claude to follow.

## Keywords
Trigger words that indicate this skill should be used.
```

### 2. Using a Skill

**In Claude.ai:**
1. Navigate to Settings > Capabilities
2. Upload the skill folder
3. Claude will automatically apply it when relevant

**In Claude Code:**
1. Place skills in your project's `.claude/skills/` directory
2. Claude Code will detect and use them automatically

**Via API:**
1. Include the skill's content in your system prompt or use the Skills API
2. Reference: [Claude Skills API Documentation](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview)

### 3. Exploring the Repository

#### Start with Examples
Browse `skills/examples/` to see how Skills are structured and documented. Each example includes:
- Clear use cases
- Detailed instructions
- Keywords for automatic triggering

#### Review Agent Patterns
Examine `agents/workflows/` to understand common patterns:
- **Prompt Chaining**: Breaking tasks into sequential steps
- **Routing**: Directing inputs to specialized handlers
- **Parallelization**: Running multiple tasks simultaneously
- **Orchestrator-Workers**: Dynamic task delegation

#### Use Templates
Copy templates from `templates/` to maintain consistency:
- Start new projects with project-specs templates
- Design APIs using api-specs templates
- Document decisions with architecture-specs templates

### 4. Creating Your First Skill

Let's create a simple code review skill:

```bash
mkdir -p skills/my-code-review
cd skills/my-code-review
```

Create `SKILL.md`:
```markdown
---
name: code-review
description: Review code following team standards
license: MIT
---

## When to use this skill
Use this skill when reviewing code, pull requests, or code snippets.

## How to use this skill

1. **Analyze the code structure**
   - Check for proper organization and separation of concerns
   - Verify naming conventions are followed

2. **Review for best practices**
   - Look for potential bugs or edge cases
   - Identify performance concerns
   - Check error handling

3. **Provide feedback**
   - List issues in order of severity (critical, important, minor)
   - Suggest specific improvements with code examples
   - Highlight what was done well

4. **Format the review**
   - Use clear headings for each section
   - Include code snippets where relevant
   - Provide actionable recommendations

## Keywords
code review, review code, check this code, pr review, pull request review
```

### 5. Working with Specs

Spec-driven development starts with clear specifications:

1. **Choose a template** from `templates/project-specs/`
2. **Fill in the sections** relevant to your project
3. **Create a skill** that references this spec format
4. **Let Claude generate** compliant artifacts

Example workflow:
```
1. User: "Create a spec for a user authentication system"
2. Claude uses spec-template skill
3. Generates structured specification document
4. User reviews and refines
5. Claude builds implementation following the spec
```

### 6. Building Agent Workflows

Start with simple patterns and increase complexity:

**Level 1: Prompt Chaining**
- Single, well-defined task broken into steps
- Each step's output feeds the next
- Good for: document generation, data transformation

**Level 2: Routing**
- Classify input and direct to appropriate handler
- Good for: customer support, multi-domain systems

**Level 3: Orchestrator-Workers**
- Dynamic task breakdown and delegation
- Good for: complex coding tasks, research projects

**Level 4: Autonomous Agents**
- LLM-driven decision making with tool access
- Good for: open-ended problems, extended workflows

See `agents/workflows/` for implementation examples.

### 7. Best Practices

**For Skills:**
- Write clear, specific instructions
- Include concrete examples
- Test with various inputs
- Document edge cases
- Use descriptive keywords

**For Specs:**
- Be thorough but concise
- Include acceptance criteria
- Define success metrics
- Document constraints
- Version your specs

**For Agents:**
- Start simple, add complexity only when needed
- Implement error handling and recovery
- Set stopping conditions
- Log decisions and actions
- Test in sandboxed environments

### 8. Common Patterns

#### Pattern: Spec-First Development
```
1. Create detailed specification
2. Build skill that enforces spec standards
3. Let Claude implement following both
4. Review and iterate
```

#### Pattern: Iterative Refinement
```
1. Initial implementation
2. Evaluator skill reviews output
3. Optimizer skill improves based on feedback
4. Repeat until criteria met
```

#### Pattern: Multi-Skill Composition
```
1. Claude analyzes task
2. Applies relevant skills automatically
3. Combines outputs coherently
4. Delivers integrated result
```

## Next Steps

1. **Explore existing Skills** in `skills/examples/`
2. **Try modifying a template** to fit your needs
3. **Create your first custom Skill** for a task you do frequently
5. **Contribute back** skills and patterns that work well

## Troubleshooting

**Skill not triggering automatically:**
- Check keywords are relevant to your query
- Verify SKILL.md format is correct
- Try explicitly mentioning the skill name

**Agent getting stuck in loops:**
- Add iteration limits
- Implement stopping conditions
- Review tool documentation clarity

**Inconsistent results:**
- Make instructions more specific
- Add concrete examples
- Test with edge cases
- Refine keywords

## Additional Resources

- [Anthropic's Building Effective Agents](https://www.anthropic.com/research/building-effective-agents)
- [Prompt Engineering Guide](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering)
- [Claude Skills Documentation](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview)

## Getting Help

- Review examples in this repository
- Check the official Anthropic documentation
- Refer to best practices in docs/best-practices/
