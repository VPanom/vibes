# Repository Agent

Autonomous agent for maintaining the vibes repository with human-in-the-loop workflow.

## What It Does

Automates common repository tasks:
- Add new skills
- Create templates
- Validate contributions
- Update documentation
- Generate examples

**Always waits for your approval before making changes.**

## Quick Start

### Using the Agent

Simply describe what you want:

```
"Add a skill for API testing"
"Create a new PRD template"
"Validate this skill"
"Update all READMEs"
"Generate examples for the docker skill"
```

The agent will:
1. Ask clarifying questions
2. Generate content
3. Show preview
4. Wait for your approval
5. Execute after you confirm

### With Claude Code

1. Reference this agent:
   ```
   "Use the repo-agent to add a skill for database migrations"
   ```

2. The agent reads `agent.md` and follows the workflows

3. You review and approve each step

### With Claude.ai

1. Upload `agent.md` to your conversation
2. Ask the agent to perform tasks
3. Review previews before approval

## Main Workflows

### Add New Skill

```
You: "Create a skill for code review"

Agent:
- Asks: category, description, keywords
- Generates: SKILL.md, directory structure
- Shows: preview of all files
- Waits: for your approval
- Creates: files after confirmation
- Updates: parent README
```

### Validate Contribution

```
You: "Validate skills/new-skill"

Agent:
- Checks: SKILL.md format
- Verifies: required sections
- Tests: structure compliance
- Reports: issues found
- Suggests: fixes (if needed)
```

### Update Documentation

```
You: "Refresh all READMEs"

Agent:
- Scans: repository for changes
- Finds: new skills/templates
- Shows: proposed updates
- Waits: for approval
- Updates: READMEs
```

## Key Features

**Human-in-the-Loop:**
- Shows preview before any action
- Waits for explicit approval
- Explains what it will do
- Asks when uncertain

**Quality Controls:**
- Follows existing patterns
- Validates format
- Checks consistency
- Maintains structure

**Safe Operations:**
- Never touches git (unless you explicitly instruct)
- Confirms before deleting
- Shows diffs for changes
- Can rollback if needed

## Validation Checks

**For Skills:**
- Has required frontmatter
- Contains all sections
- Keywords present
- Examples exist
- Listed in parent README
- Reasonable length (<200 lines preferred)

**For Templates:**
- Has metadata header
- Standard sections included
- Proper markdown format
- Parent README updated

## Configuration

No configuration needed - the agent adapts to the repository structure.

## Examples

See `examples/common-tasks.md` for detailed interaction examples.

## Tips

**Getting best results:**
- Be specific about what you want
- Review previews carefully
- Provide feedback on generated content
- Reference existing skills/templates as examples

**Common patterns:**
```
"Add a skill like conventional-commits but for X"
"Create a template similar to PRD but for Y"
"Validate everything in skills/new-category"
```

## Limitations

**Agent will NOT:**
- Make git commits/pushes (unless you explicitly instruct)
- Delete files without confirmation
- Modify core docs without approval
- Assume or guess requirements

**Agent will ask for help when:**
- Requirements unclear
- Pattern doesn't exist
- Conflicts with existing content
- Validation fails

## Troubleshooting

**Agent not following patterns:**
- Show it an example skill/template to reference
- Be more specific about requirements

**Validation too strict:**
- Ask to proceed despite warnings
- Fix issues manually then re-validate

**Preview doesn't look right:**
- Say "edit" instead of "yes"
- Provide specific feedback
- Ask to regenerate with changes

## Related

- [Building Effective Agents](https://www.anthropic.com/research/building-effective-agents)
- [Repository Architecture](../../ARCHITECTURE.md)
- [Skills README](../../skills/README.md)
