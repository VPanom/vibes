# Spec Template Skills

Skills for generating, validating, and working with specifications in a structured, consistent manner.

## Overview

These skills teach Claude how to create and work with various types of specifications, ensuring consistency across projects and alignment with organizational standards.

## Available Skills

### spec-generator
Generates structured specifications based on project type and requirements.

**Triggers:** "create a spec", "generate specification", "need a requirements document"

**Outputs:** Formatted specification documents following standard templates

### spec-validator
Validates specifications for completeness, clarity, and adherence to standards.

**Triggers:** "review this spec", "validate specification", "check requirements"

**Outputs:** Validation report with issues and suggestions

### prd-writer
Creates Product Requirements Documents for new features or products.

**Triggers:** "write PRD", "product requirements", "feature specification"

**Outputs:** Comprehensive PRD with all standard sections

### api-spec-designer
Designs API specifications including endpoints, parameters, and contracts.

**Triggers:** "design API", "API specification", "endpoint documentation"

**Outputs:** Complete API specification in OpenAPI or custom format

### adr-creator
Creates Architecture Decision Records documenting technical decisions.

**Triggers:** "document decision", "create ADR", "architecture decision"

**Outputs:** Structured ADR with context, decision, and consequences

## Using These Skills

### Basic Usage

Upload the skill folder to Claude and it will automatically apply when relevant:

```
User: "I need to create a spec for a new authentication system"
Claude: [Applies prd-writer or spec-generator skill]
```

### Explicit Invocation

You can explicitly request a skill:

```
User: "Use the API spec designer to create an endpoint for user registration"
Claude: [Applies api-spec-designer skill]
```

### Skill Composition

Multiple skills can work together:

```
User: "Create a complete project spec including API design"
Claude: [Applies spec-generator + api-spec-designer]
```

## Skill Development

### Creating a New Spec Skill

1. **Identify the need**: What type of specification is frequently needed?
2. **Define the structure**: What sections should it include?
3. **Create examples**: What does a good version look like?
4. **Write instructions**: How should Claude create this spec?
5. **Test thoroughly**: Does it work across different scenarios?

### Template

```markdown
---
name: your-spec-skill
description: Brief description of what specs this creates
license: MIT
---

## When to use this skill
Describe when Claude should use this skill.

## How to use this skill

1. **Gather requirements**
   - Ask clarifying questions
   - Understand scope and constraints

2. **Structure the specification**
   - Use standard template
   - Organize sections logically

3. **Fill in details**
   - Write clear, specific requirements
   - Include examples and edge cases

4. **Format and deliver**
   - Use proper markdown formatting
   - Include all standard sections

## Keywords
trigger phrases, related terms
```

## Best Practices

### For Spec Generation

**Ask Clarifying Questions:**
Don't assume - gather complete information before generating specs.

**Use Concrete Examples:**
Include specific examples to illustrate requirements.

**Be Comprehensive:**
Cover all aspects including edge cases, errors, and non-functional requirements.

**Structure Logically:**
Organize information in a clear, navigable structure.

**Include Metadata:**
Add version, author, date, status, and other tracking information.

### For Spec Validation

**Check Completeness:**
Ensure all required sections are present and filled in.

**Verify Clarity:**
Look for vague language, ambiguity, and missing definitions.

**Assess Feasibility:**
Identify unrealistic requirements or conflicting constraints.

**Review Consistency:**
Check for internal contradictions and alignment with standards.

## Integration Patterns

### With Development Workflows

```
1. Generate spec using spec-generator skill
2. Review and refine with stakeholders  
3. Validate with spec-validator skill
4. Use spec to guide implementation
5. Update spec as implementation evolves
```

### With Other Skills

Spec skills work well with:
- **Code generation skills**: Implement based on specs
- **Review skills**: Validate implementation matches spec
- **Documentation skills**: Generate docs from specs
- **Testing skills**: Create tests based on spec criteria

## Customization

### Organizational Standards

Modify skills to include:
- Company-specific sections
- Required approval workflows
- Standard terminology
- Compliance requirements
- Tool/framework preferences

### Domain-Specific Variants

Create specialized versions for:
- Healthcare (HIPAA compliance)
- Finance (regulatory requirements)
- E-commerce (payment processing)
- Mobile apps (platform-specific needs)
- IoT (hardware constraints)

## Common Scenarios

### New Feature Development

```
User: "We need a notification system for the app"
Claude: 
1. Applies prd-writer skill
2. Asks about notification types, delivery methods, platforms
3. Generates comprehensive feature specification
4. Includes user stories, technical requirements, success metrics
```

### API Design

```
User: "Design an API for managing user profiles"
Claude:
1. Applies api-spec-designer skill
2. Defines endpoints (GET, POST, PUT, DELETE)
3. Specifies request/response formats
4. Documents authentication, errors, rate limits
5. Creates OpenAPI specification
```

### Architecture Decisions

```
User: "We need to decide between PostgreSQL and MongoDB"
Claude:
1. Applies adr-creator skill
2. Documents context and requirements
3. Evaluates options with pros/cons
4. Records decision and rationale
5. Notes consequences and follow-up actions
```

## Troubleshooting

### Specs Too Generic

**Problem:** Generated specs lack project-specific details

**Solution:**
- Provide more context upfront
- Answer clarifying questions thoroughly
- Include examples from your domain
- Reference existing project documentation

### Missing Sections

**Problem:** Important sections omitted

**Solution:**
- Review skill's section checklist
- Explicitly request missing sections
- Update skill to include by default
- Use spec-validator to catch gaps

### Inconsistent Format

**Problem:** Specs don't follow standard format

**Solution:**
- Reference template explicitly in skill
- Include formatting examples
- Use validation skill to enforce standards
- Create organization-specific skill variant

## Examples

Each skill directory contains:
- Complete SKILL.md file
- Example specifications generated
- Usage scenarios
- Customization guide

## Resources

- [Templates Directory](../../templates/) - Base templates these skills use
- [Spec-Driven Development Guide](../../docs/best-practices/spec-driven-development.md)
- [Writing Requirements](../../docs/best-practices/requirements-writing.md)

## Contributing

When contributing spec skills:

1. Ensure alignment with existing templates
2. Include comprehensive examples
3. Test with varied inputs
4. Document customization options
5. Provide clear usage guidance
