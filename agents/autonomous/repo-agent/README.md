# Repository Agent Reference

This directory contains reference documentation and examples for the repository agent.

## Main Agent

The primary agent definition is located at the repository root: `/agent.md`

This allows Claude Code and other tools to automatically discover and use the agent for all repository operations.

## Contents

- **REFERENCE.md** - Detailed setup and usage guide
- **examples/** - Real interaction examples showing common tasks

## Quick Start

The agent is automatically active when working in this repository. Simply describe what you want:

```
"Add a skill for database migrations"
"Validate this new template"
"Update all READMEs"
```

See `REFERENCE.md` for complete documentation and `examples/` for detailed interaction examples.

## Agent Capabilities

- Add new skills and templates
- Validate contributions
- Update documentation
- Generate examples
- Maintain repository consistency

All operations use human-in-the-loop - the agent shows previews and waits for your approval before making changes.
