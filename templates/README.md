# Templates

This directory contains spec-driven development templates for maintaining consistency across projects, APIs, and architectural decisions.

## Overview

Spec-driven development uses detailed specifications to guide AI-assisted development, ensuring clarity, consistency, and alignment with requirements. These templates provide structured starting points for common specification needs.

## Structure

- **project-specs/** - Product requirements and project specifications
- **api-specs/** - API design and contract templates
- **architecture-specs/** - Architecture decision records and system design

## Template Categories

### Project Specifications

Templates for defining project scope, requirements, and deliverables.

**Included templates:**
- Product Requirements Document (PRD)
- Technical Specification
- Feature Specification
- Project Brief
- User Stories Template

**When to use:**
- Starting new projects
- Defining features
- Aligning stakeholders
- Planning sprints

### API Specifications

Templates for designing and documenting APIs.

**Included templates:**
- REST API Contract
- GraphQL Schema
- WebSocket Protocol
- API Integration Guide
- Endpoint Documentation

**When to use:**
- Designing new APIs
- Documenting existing endpoints
- Planning integrations
- Establishing contracts

### Architecture Specifications

Templates for documenting architectural decisions and system designs.

**Included templates:**
- Architecture Decision Record (ADR)
- System Design Document
- Technical Architecture Overview
- Database Schema Design
- Infrastructure Specification

**When to use:**
- Making architectural decisions
- Designing systems
- Documenting trade-offs
- Planning migrations

## Using Templates

### Basic Workflow

1. **Select appropriate template** for your need
2. **Copy template** to your project
3. **Fill in sections** with project-specific details
4. **Review with stakeholders** for completeness
5. **Use as reference** during implementation

### With Claude

Templates work exceptionally well with Claude:

```
1. Upload template to Claude
2. Provide project context
3. Claude fills in template sections
4. Review and refine
5. Use completed spec to guide development
```

### Creating Skills from Templates

You can create Skills that automatically use these templates:

```markdown
---
name: prd-generator
description: Generate product requirement documents using standard template
---

## When to use this skill
Use when creating product requirement documents or feature specifications.

## How to use this skill

1. Load the PRD template from templates/project-specs/
2. Ask clarifying questions to gather requirements
3. Fill in template sections systematically
4. Ensure all sections are complete
5. Format as professional document
```

## Template Structure

Each template follows this pattern:

### Header Section
- Document title
- Version information
- Author/owner
- Date created/modified
- Status (draft, review, approved)

### Overview Section
- Purpose and goals
- Scope and boundaries
- Target audience
- Key stakeholders

### Details Section
- Specific requirements
- Technical details
- Acceptance criteria
- Dependencies

### Supporting Information
- Context and background
- Assumptions
- Constraints
- References

## Best Practices

### Writing Specifications

**Be Specific:**
- Use concrete, measurable criteria
- Avoid vague language
- Include examples
- Define success explicitly

**Be Complete:**
- Cover all requirements
- Document edge cases
- Include non-functional requirements
- List dependencies

**Be Clear:**
- Use simple language
- Define technical terms
- Structure logically
- Use diagrams where helpful

**Be Realistic:**
- Consider constraints
- Account for trade-offs
- Include timelines
- Note risks

### Maintaining Specifications

**Version Control:**
- Track all changes
- Document revisions
- Maintain history
- Tag releases

**Review Process:**
- Regular reviews
- Stakeholder approval
- Update as needed
- Archive outdated versions

**Accessibility:**
- Central storage
- Easy to find
- Well organized
- Searchable

## Template Format Standards

### Markdown Guidelines

Use consistent formatting:

```markdown
# Level 1: Document Title
## Level 2: Major Sections
### Level 3: Subsections
#### Level 4: Detailed Items

**Bold** for emphasis
*Italic* for technical terms
`code` for technical references
> Blockquotes for important notes
```

### Section Ordering

Standard section order:
1. Header/Metadata
2. Executive Summary
3. Overview
4. Requirements/Details
5. Technical Specifications
6. Implementation Notes
7. Appendices

### Metadata Fields

Include at minimum:
- Document ID/Version
- Title
- Author
- Date
- Status
- Reviewers
- Related Documents

## Integration with Development

### Spec-First Development

```
Specification → Implementation → Validation
```

Benefits:
- Clear requirements
- Reduced ambiguity
- Better estimates
- Easier reviews
- Consistent results

### Spec-Driven AI Development

Using specs with Claude:

1. **Create detailed spec** using templates
2. **Reference spec** in prompts
3. **Claude implements** following spec
4. **Validate** against spec criteria
5. **Iterate** until spec satisfied

### Continuous Validation

Keep specs and code synchronized:
- Reference specs in code comments
- Update specs with implementation changes
- Use specs in automated tests
- Review specs during code review

## Customizing Templates

### For Your Organization

Adapt templates to your needs:

1. **Add organization-specific sections**
   - Compliance requirements
   - Standard tools/frameworks
   - Approval workflows
   - Company terminology

2. **Modify format**
   - Adjust section order
   - Add/remove sections
   - Change detail level
   - Update examples

3. **Create variants**
   - Different project types
   - Various complexity levels
   - Department-specific versions
   - Client-facing vs internal

### For Different Domains

Templates can be specialized:

- **Frontend**: UI/UX specifications, component libraries
- **Backend**: Data models, API contracts, business logic
- **Infrastructure**: Deployment specs, scaling requirements
- **Mobile**: Platform-specific requirements, offline behavior
- **Data**: Schema design, ETL specifications, data governance

## Examples

See individual template directories for:
- Complete template files
- Filled examples
- Usage guidance
- Common variations

## Common Pitfalls

### Too Vague
Problem: "System should be fast"
Better: "API responses must complete within 200ms for 95% of requests"

### Too Prescriptive
Problem: Specifying exact implementation details
Better: Specify requirements and constraints, allow implementation flexibility

### Incomplete
Problem: Missing edge cases, error scenarios
Better: Systematically cover normal and exceptional cases

### Outdated
Problem: Spec doesn't match implementation
Better: Treat specs as living documents, update with changes

## Template Maintenance

### Regular Review

Schedule periodic reviews:
- Quarterly template audits
- Update based on feedback
- Incorporate lessons learned
- Remove outdated sections

### Version Management

Track template versions:
- Semantic versioning
- Change logs
- Migration guides
- Backward compatibility notes

### Community Contributions

Improve templates through:
- User feedback
- Real-world usage
- Best practice updates
- Domain expertise

## Resources

- [Spec-Driven Development Guide](../docs/best-practices/spec-driven-development.md)
- [Writing Effective Requirements](../docs/best-practices/requirements-writing.md)
- [Architecture Decision Records](https://adr.github.io/)
- [API Design Best Practices](https://docs.anthropic.com/en/api/overview)

## Contributing Templates

When adding templates:

1. Follow established format patterns
2. Include complete examples
3. Document all sections clearly
4. Test with real projects
5. Provide usage guidance
6. Consider various use cases
