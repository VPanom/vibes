# ADR [Number]: [Short Title in Noun Form]

**Status:** [Proposed | Accepted | Deprecated | Superseded]  
**Date:** [YYYY-MM-DD]  
**Authors:** [Names]  
**Reviewers:** [Names]  
**Supersedes:** [ADR number if applicable]  
**Superseded by:** [ADR number if applicable]  

## Context

[Describe the forces at play, including technological, political, social, and project-level considerations. This section should be factual and objective, describing the situation and constraints that led to the need for a decision.]

### Background
[What is the current situation? What problem are we trying to solve?]

### Constraints
- [Constraint 1: e.g., budget, time, technology, team skills]
- [Constraint 2]
- [Constraint 3]

### Requirements
- [Requirement 1: What must the solution accomplish?]
- [Requirement 2]
- [Requirement 3]

### Stakeholders
- [Stakeholder group and their concerns]
- [Stakeholder group and their concerns]

## Decision

[State the decision clearly and concisely. Use active voice: "We will..."]

We will [specific decision].

### Rationale
[Explain why this decision was made. What factors were most important? What trade-offs were considered?]

## Alternatives Considered

### Alternative 1: [Name]

**Description:**
[Describe this alternative approach]

**Pros:**
- [Advantage 1]
- [Advantage 2]

**Cons:**
- [Disadvantage 1]
- [Disadvantage 2]

**Why not chosen:**
[Explain why this option was rejected]

### Alternative 2: [Name]

[Follow same format as Alternative 1]

### Alternative 3: [Name]

[Follow same format as Alternative 1]

## Consequences

### Positive Consequences
- [Benefit 1: What does this decision enable or improve?]
- [Benefit 2]
- [Benefit 3]

### Negative Consequences
- [Cost 1: What are the downsides or limitations?]
- [Cost 2]
- [Cost 3]

### Risks
| Risk | Likelihood | Impact | Mitigation |
|------|------------|--------|------------|
| [Risk 1] | [H/M/L] | [H/M/L] | [How to address] |
| [Risk 2] | [H/M/L] | [H/M/L] | [How to address] |

### Trade-offs
- [Trade-off 1: What are we sacrificing for what gain?]
- [Trade-off 2]

## Implementation

### Action Items
- [ ] [Specific task required to implement this decision]
- [ ] [Specific task required to implement this decision]
- [ ] [Specific task required to implement this decision]

### Timeline
[Expected timeline for implementation]

### Success Criteria
- [How will we know this decision was successful?]
- [What metrics will we track?]

## Follow-up

### Review Date
[When should this decision be reviewed or reconsidered?]

### Monitoring
[What should we monitor to ensure this decision remains valid?]

### Related Decisions
- [Link to related ADR]
- [Link to related ADR]

## References

- [Link to relevant documentation]
- [Link to research or article]
- [Link to discussion or RFC]

## Notes

[Any additional context, discussion points, or considerations that don't fit elsewhere]

---

## ADR Template Guide

### When to Create an ADR

Create an ADR for decisions that:
- Have significant impact on the system architecture
- Are difficult or expensive to reverse
- Affect multiple teams or systems
- Establish patterns to be followed
- Involve significant trade-offs
- Need to be communicated broadly

### Writing Tips

**Context Section:**
- Be objective and factual
- Describe the situation, not the solution
- Include enough background for future readers
- Document constraints that influenced the decision
- Reference related documents or discussions

**Decision Section:**
- State clearly in active voice
- Be specific and actionable
- Explain the "why" not just the "what"
- Keep it concise but complete

**Alternatives:**
- Include all seriously considered options
- Be fair to each alternative
- Document why they weren't chosen
- This helps future readers understand the thinking

**Consequences:**
- Be honest about downsides
- Include both immediate and long-term effects
- Consider technical, social, and organizational impacts
- Think about reversibility

### Status Meanings

- **Proposed**: Decision is under discussion
- **Accepted**: Decision has been approved and is being implemented
- **Deprecated**: Decision is no longer recommended but may still be in use
- **Superseded**: Decision has been replaced by a newer ADR (reference it)

### Numbering Convention

Use sequential numbering (e.g., ADR-001, ADR-002) or date-based (e.g., ADR-20260211-database-choice).

### Storage and Organization

Store ADRs in:
- Version control with code (e.g., `/docs/adr/`)
- Chronological order by number
- With links in main documentation

### Review and Updates

- Review ADRs periodically (quarterly or annually)
- Update status as decisions evolve
- Create new ADRs to supersede old ones rather than editing
- Maintain history of architectural evolution

### Example ADR Titles

Good titles are short noun phrases:
- "Use PostgreSQL for Primary Database"
- "Adopt Microservices Architecture"
- "Switch to JWT for Authentication"
- "Implement GraphQL API Layer"

Avoid:
- Verb forms: "Using PostgreSQL"
- Questions: "Should we use PostgreSQL?"
- Too generic: "Database Choice"
