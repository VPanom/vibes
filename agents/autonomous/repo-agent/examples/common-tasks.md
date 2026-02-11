# Common Tasks Examples

Real interaction examples with the repository agent.

## Adding a New Skill

### Simple Skill

```
User: "Create a skill for writing unit tests"

Agent:
I'll help create a unit testing skill.

Questions:
1. Category? (spec-templates/prompt-engineering/agents/examples)
   → prompt-engineering

2. Brief description?
   → Generate unit tests following best practices and testing patterns

3. Main keywords?
   → unit test, testing, test cases, jest, pytest, testing patterns

Generated structure:
skills/prompt-engineering/unit-testing/
├── SKILL.md
└── examples/
    └── examples.md

Preview SKILL.md:
---
name: unit-testing
description: Generate unit tests following best practices and testing patterns
license: MIT
---

## When to use this skill
Use when writing unit tests for functions, classes, or modules.

## How to use this skill

### Test Structure
- Arrange: Set up test data
- Act: Execute the code
- Assert: Verify results

### Best Practices
- One assertion per test (preferred)
- Clear test names describing what's tested
- Test edge cases and error conditions
- Mock external dependencies

[... more content ...]

## Keywords
unit test, testing, test cases, jest, pytest, testing patterns

---

Approve? (yes/no/edit)

User: yes

Agent:
✓ Created skills/prompt-engineering/unit-testing/SKILL.md
✓ Created skills/prompt-engineering/unit-testing/examples/examples.md
✓ Updated skills/prompt-engineering/README.md

Done! Test the skill with: "Write unit tests for this function"
```

### Skill with Resources

```
User: "Add a skill for Kubernetes configurations with example manifests"

Agent:
I'll create a Kubernetes configuration skill with resource files.

Questions:
1. Category? → prompt-engineering
2. Brief description? → Generate Kubernetes manifests following best practices
3. Keywords? → kubernetes, k8s, manifests, deployment, service

Generated structure:
skills/prompt-engineering/k8s-config/
├── SKILL.md
├── examples/
│   └── examples.md
└── resources/
    ├── deployment-template.yaml
    ├── service-template.yaml
    └── configmap-template.yaml

[Shows SKILL.md and resource files preview]

Approve? (yes/no/edit)

User: yes

Agent:
✓ Created all files
✓ Updated parent README

Done!
```

## Validating Content

### Validate New Skill

```
User: "Validate skills/prompt-engineering/api-testing"

Agent:
Validating skill: api-testing

Checks:
✓ SKILL.md exists
✓ Has frontmatter (name, description, license)
✓ Has "When to use this skill" section
✓ Has "How to use this skill" section
✓ Has Keywords section
✓ Keywords are lowercase and comma-separated
✓ Examples directory exists
✗ Not listed in skills/prompt-engineering/README.md
⚠ SKILL.md is 187 lines (under 200 - good)

Issues found:
1. Skill not added to parent README

Fix automatically? (yes/no)

User: yes

Agent:
✓ Added api-testing to skills/prompt-engineering/README.md

Validation complete! All checks passing.
```

### Validate with Errors

```
User: "Validate skills/examples/broken-skill"

Agent:
Validating skill: broken-skill

Checks:
✓ SKILL.md exists
✗ Missing frontmatter
✗ No "When to use this skill" section
✗ No "Keywords" section
✓ Examples directory exists

Critical issues found:
1. SKILL.md missing required frontmatter
2. Missing "When to use this skill" section
3. Missing Keywords section

Cannot auto-fix critical issues.

Options:
1. Fix manually and re-validate
2. Show example of correct format
3. Regenerate SKILL.md from scratch

What would you like to do? (1/2/3)

User: 2

Agent:
Here's the required format:

---
name: skill-name
description: Brief one-line description
license: MIT
---

## When to use this skill
Clear description of when to use this skill

## How to use this skill
Instructions...

## Keywords
keyword1, keyword2, keyword3

Would you like me to help fix broken-skill? (yes/no)
```

## Creating Templates

### Simple Template

```
User: "Create a bug report template"

Agent:
I'll create a bug report template.

Questions:
1. Category? (project-specs/api-specs/architecture-specs)
   → project-specs

2. Key sections needed?
   → description, steps to reproduce, expected vs actual, environment, screenshots

Generated template:
templates/project-specs/bug-report.md

Preview:
# Bug Report

**Version:** 1.0
**Date:** 2026-02-11
**Status:** Template

## Bug Description
[Clear, concise description of the bug]

## Steps to Reproduce
1. [First step]
2. [Second step]
3. [...]

## Expected Behavior
[What should happen]

## Actual Behavior
[What actually happens]

## Environment
- OS: [e.g., Ubuntu 22.04]
- Browser: [e.g., Chrome 120]
- Version: [e.g., v2.1.0]

## Screenshots
[If applicable, add screenshots]

## Additional Context
[Any other relevant information]

---

Approve? (yes/no/edit)

User: yes

Agent:
✓ Created templates/project-specs/bug-report.md
✓ Updated templates/project-specs/README.md

Done!
```

## Updating Documentation

### Update Single README

```
User: "Update skills/prompt-engineering/README.md"

Agent:
Scanning skills/prompt-engineering/ for changes...

Found:
- unit-testing (not in README)
- k8s-config (not in README)
- api-testing (already listed)

Proposed changes to README.md:
```diff
 ## Available Skills
 
 ### api-testing
 Test API endpoints and validate responses.
 
+### k8s-config
+Generate Kubernetes manifests following best practices.
+
+### unit-testing
+Generate unit tests following best practices and testing patterns.
```

Apply changes? (yes/no)

User: yes

Agent:
✓ Updated skills/prompt-engineering/README.md

Done!
```

### Update All READMEs

```
User: "Refresh all documentation"

Agent:
Scanning repository...

Updates needed:

1. skills/spec-templates/README.md
   + Add new-spec-skill

2. templates/api-specs/README.md  
   + Add graphql-template.md

3. skills/prompt-engineering/README.md
   + Add docker-config
   + Add terraform-config

Show detailed preview? (yes/no)

User: yes

Agent:
[Shows all diffs]

Apply all updates? (yes/no/selective)

User: yes

Agent:
✓ Updated skills/spec-templates/README.md
✓ Updated templates/api-specs/README.md
✓ Updated skills/prompt-engineering/README.md

3 READMEs updated, 4 entries added.
```

## Generating Examples

### Generate Examples for Skill

```
User: "Generate examples for the unit-testing skill"

Agent:
Analyzing skills/prompt-engineering/unit-testing/SKILL.md...

Identified use cases:
- Testing functions
- Testing classes
- Testing async code
- Testing edge cases
- Mocking dependencies

Generating examples...

Preview examples/examples.md:
# Unit Testing Examples

## Simple Function Test
```javascript
// Function to test
function add(a, b) {
  return a + b;
}

// Unit test
test('add returns sum of two numbers', () => {
  expect(add(2, 3)).toBe(5);
});
```

## Testing Edge Cases
```javascript
test('add handles zero', () => {
  expect(add(0, 5)).toBe(5);
  expect(add(5, 0)).toBe(5);
});

test('add handles negative numbers', () => {
  expect(add(-2, 3)).toBe(1);
});
```

[... more examples ...]

---

Use these examples? (yes/no/edit)

User: yes

Agent:
✓ Created skills/prompt-engineering/unit-testing/examples/examples.md

Done!
```

## Error Handling

### File Already Exists

```
User: "Create a skill for Docker"

Agent:
Error: skills/prompt-engineering/docker/ already exists

Options:
1. Use different name (docker-compose, docker-advanced, etc.)
2. Update existing skill
3. Cancel

What would you like to do? (1/2/3)

User: 1, call it docker-compose

Agent:
Creating docker-compose skill...
[continues normally]
```

### Uncertain About Pattern

```
User: "Add a skill for quantum computing algorithms"

Agent:
I'll create a quantum computing skill.

Note: This is a specialized domain. I don't see similar skills
in the repository to use as reference.

Would you like to:
1. Proceed with standard skill format
2. Provide an example skill to reference
3. Create together with more guidance

Recommend: Option 3 for specialized topics

What would you like to do? (1/2/3)
```
