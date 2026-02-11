---
name: conventional-commits
description: Generate git commit messages following Conventional Commits v1.0.0 specification for automated changelog generation and semantic versioning.
license: MIT
---

## When to use this skill

Use when creating git commit messages that need to follow the Conventional Commits standard.

## How to use this skill

### Format

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

### Types

- `feat`: New feature (MINOR version)
- `fix`: Bug fix (PATCH version)
- `docs`: Documentation only
- `style`: Formatting, semicolons, etc.
- `refactor`: Code change, no bug fix or feature
- `perf`: Performance improvement
- `test`: Adding/updating tests
- `build`: Build system or dependencies
- `ci`: CI configuration
- `chore`: Maintenance tasks
- `revert`: Revert previous commit

### Rules

1. **Description**: Use imperative mood ("add" not "added"), lowercase, no period
2. **Scope**: Optional, lowercase, in parentheses: `feat(api):`
3. **Breaking changes**: Add `!` after type/scope: `feat!:` or `feat(api)!:`
4. **Body**: Optional, separated by blank line, explain why
5. **Footer**: Optional, for breaking changes, issues: `BREAKING CHANGE:`, `Refs: #123`

### Breaking Changes

```
feat!: remove deprecated API endpoints

BREAKING CHANGE: The /v1/users endpoint is removed. Use /v2/users instead.

Migration guide: docs/api/migration.md
```

### Examples

**Simple:**
```
feat: add user login
fix(api): resolve timeout issue
docs: update installation guide
```

**With scope:**
```
feat(auth): add OAuth2 support
fix(database): prevent connection leak
```

**With body:**
```
fix(parser): handle empty input

Previously threw error on empty strings.
Now returns empty result as expected.

Fixes: #123
```

**Breaking change:**
```
feat(api)!: redesign authentication

BREAKING CHANGE: Auth header changed from X-API-Key to Authorization: Bearer.
Update all API clients.
```

## Git Hook

Save as `.git/hooks/commit-msg`:

```bash
#!/bin/sh
msg=$(cat "$1")
pattern='^(feat|fix|docs|style|refactor|perf|test|build|ci|chore|revert)(\([a-z0-9-]+\))?!?: .+'

if ! echo "$msg" | grep -qE "$pattern"; then
    echo "❌ Invalid commit format"
    echo "Use: <type>[scope]: <description>"
    echo "Example: feat(api): add user endpoint"
    exit 1
fi
```

Make executable: `chmod +x .git/hooks/commit-msg`

## Keywords

commit message, git commit, conventional commit, semantic commit, changelog
