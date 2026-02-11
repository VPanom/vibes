---
name: spec-generator
description: Generate comprehensive, structured specifications for projects, features, and systems following industry best practices and organizational standards.
license: MIT
---

## When to use this skill

Use this skill whenever you need to create a specification document, including:
- Product Requirements Documents (PRDs)
- Technical specifications
- Feature specifications
- System design documents
- Project proposals
- API contracts
- Architecture decision records

This skill ensures specifications are complete, well-structured, and follow consistent formatting.

## How to use this skill

### 1. Identify the specification type

Determine what kind of specification is needed based on the request:
- **Product/Feature**: PRD or feature specification
- **API/Interface**: API contract or interface specification
- **Architecture**: System design or architecture decision record
- **Project**: Project proposal or technical specification

### 2. Gather comprehensive requirements

Before generating the specification, collect essential information through targeted questions:

**For Product/Feature Specs:**
- What problem does this solve?
- Who are the target users?
- What are the key features/capabilities?
- What are the success metrics?
- Are there any constraints or dependencies?

**For Technical Specs:**
- What is the technical scope?
- What are the system requirements?
- What technologies/frameworks are involved?
- What are the performance requirements?
- What are the security/compliance needs?

**For API Specs:**
- What resources/entities are being exposed?
- What operations are needed (CRUD, etc.)?
- What are the authentication requirements?
- What data formats are expected?
- What error scenarios must be handled?

**For Architecture Decisions:**
- What decision needs to be made?
- What options are being considered?
- What are the evaluation criteria?
- What are the trade-offs?
- Who are the decision makers?

### 3. Structure the specification

Use the appropriate template structure from `resources/templates/`:

**Standard Specification Structure:**
```
# [Title]

## Metadata
- Version
- Author
- Date
- Status
- Reviewers

## Executive Summary
High-level overview in 2-3 paragraphs

## Background/Context
Why this specification exists

## Goals and Objectives
What we're trying to achieve

## Requirements
Detailed functional and non-functional requirements

## Technical Specifications
Implementation details, architecture, data models

## Success Criteria
How we measure completion and success

## Timeline and Milestones
Key dates and deliverables

## Risks and Mitigations
Potential issues and how to address them

## Appendices
Supporting information, references, diagrams
```

### 4. Write clear, specific content

Follow these principles when filling in each section:

**Be Specific and Measurable:**
- Use concrete, quantifiable criteria
- Avoid vague language like "fast", "good", "user-friendly"
- Include examples and specific scenarios
- Define clear acceptance criteria

**Be Comprehensive:**
- Cover both functional and non-functional requirements
- Document edge cases and error scenarios
- Include dependencies and constraints
- Note assumptions explicitly

**Be Clear and Concise:**
- Use simple, direct language
- Define technical terms on first use
- Structure information logically
- Use bullet points and tables for clarity

**Be Realistic:**
- Consider actual constraints (time, resources, technology)
- Acknowledge trade-offs
- Include risk assessment
- Set achievable goals

### 5. Format professionally

Use consistent Markdown formatting:

**Headers:**
```markdown
# Document Title (H1)
## Major Sections (H2)
### Subsections (H3)
#### Detailed Items (H4)
```

**Emphasis:**
- **Bold** for key terms and important points
- *Italic* for technical terms on first use
- `code` for technical references, file names, API endpoints

**Lists:**
- Use numbered lists for sequences and priorities
- Use bullet points for unordered items
- Nest lists for hierarchical information

**Tables:**
Use for structured data like requirements matrices, API endpoints, etc.

**Code Blocks:**
Use fenced code blocks with language specification for examples

### 6. Include all required sections

Ensure completeness by checking against this checklist:

- [ ] Metadata (version, author, date, status)
- [ ] Executive summary
- [ ] Background/context
- [ ] Goals and objectives
- [ ] Detailed requirements
- [ ] Technical specifications (if applicable)
- [ ] Success criteria and metrics
- [ ] Timeline/milestones (if applicable)
- [ ] Risks and mitigations
- [ ] Dependencies
- [ ] Assumptions
- [ ] References/appendices

### 7. Provide actionable next steps

End specifications with clear next steps:
- What approvals are needed
- Who needs to review
- What decisions must be made
- When implementation should start
- What follow-up documentation is needed

## Special cases

### API Specifications

For API specs, include:
- Base URL and versioning strategy
- Authentication/authorization mechanisms
- All endpoints with HTTP methods
- Request/response formats with examples
- Error codes and messages
- Rate limiting and pagination
- Deprecation policy

Use OpenAPI (Swagger) format when appropriate.

### Architecture Decision Records

For ADRs, use this structure:
1. **Title**: Short noun phrase
2. **Status**: Proposed, Accepted, Deprecated, Superseded
3. **Context**: Forces at play, constraints, requirements
4. **Decision**: What we decided and why
5. **Consequences**: Positive and negative outcomes
6. **Alternatives Considered**: Other options and why rejected

### Product Requirements Documents

For PRDs, emphasize:
- User stories and personas
- User journey/flow
- UI/UX considerations
- Competitive analysis
- Go-to-market considerations
- Success metrics and KPIs

## Quality checks

Before finalizing, verify:

1. **Completeness**: All sections present and filled in
2. **Clarity**: No ambiguous or vague language
3. **Consistency**: No internal contradictions
4. **Feasibility**: Requirements are realistic
5. **Traceability**: Requirements linked to goals
6. **Testability**: Clear acceptance criteria
7. **Maintainability**: Versioned and easy to update

## Example output format

```markdown
# User Authentication System Specification

**Version:** 1.0  
**Author:** Engineering Team  
**Date:** 2026-02-11  
**Status:** Draft  
**Reviewers:** Product, Security, Engineering  

## Executive Summary

This specification defines a secure user authentication system supporting email/password and OAuth2 social login (Google, GitHub). The system will handle 100,000 daily active users with 99.9% uptime, implementing industry-standard security practices including bcrypt password hashing, JWT tokens, and rate limiting.

## Background

Our application currently lacks user authentication, limiting our ability to provide personalized experiences and secure user data. This specification addresses the need for a robust, scalable authentication system.

## Goals and Objectives

**Primary Goals:**
- Implement secure user authentication and authorization
- Support multiple authentication methods
- Ensure high availability and performance
- Comply with security best practices and regulations

**Success Metrics:**
- 99.9% uptime
- < 200ms average authentication latency
- Zero critical security vulnerabilities
- 90% user satisfaction with login experience

[... continues with detailed sections ...]
```

## Keywords

create specification, write spec, generate spec, need a spec, specification document, requirements document, PRD, product requirements, technical spec, API specification, system design, architecture decision, feature spec, project proposal, write requirements, document requirements

## Resources

This skill references templates in the `resources/templates/` directory:
- `prd-template.md` - Product Requirements Document template
- `technical-spec-template.md` - Technical specification template
- `api-spec-template.md` - API contract template
- `adr-template.md` - Architecture Decision Record template
- `feature-spec-template.md` - Feature specification template
