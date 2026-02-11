# Conventional Commit Examples

## Features
```
feat: add user registration
feat(api): add pagination to list endpoint
feat(auth): implement OAuth2 login
```

## Fixes
```
fix: prevent null pointer exception
fix(api): resolve timeout on large requests
fix(ui): correct button alignment on mobile
```

## Breaking Changes
```
feat!: remove deprecated v1 endpoints

BREAKING CHANGE: All /v1/* endpoints removed. Use /v2/* instead.
```

```
refactor(api)!: change response format

BREAKING CHANGE: Responses now wrapped in { data, meta }.
Update all API clients accordingly.

Migration: docs/api-migration.md
```

## With Body and Footers
```
fix(database): prevent connection pool exhaustion

Added timeout and cleanup to prevent pool exhaustion under
high load. Connections now properly released.

Fixes: #456
Reviewed-by: Database Team
```

## Common Scenarios
```
docs: update README installation steps
style: format code with prettier
refactor: extract validation to middleware
perf(db): add indexes to user table
test: add edge case coverage for parser
build(deps): upgrade react to 18.2.0
ci: add automated release workflow
chore: update .gitignore
```
