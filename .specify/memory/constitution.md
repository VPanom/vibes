<!--
  Sync Impact Report - Constitution Update
  
  Version Change: 1.0.0 → 1.1.0
  
  Modified Principles:
  - III. Documentation as Contract → III. Token-Efficient Communication (redefined focus)
  
  Added Sections: None
  
  Removed Sections: None
  
  Templates Requiring Updates:
  - ✅ .specify/templates/plan-template.md (Gate 1 checklist item updated to reference Principle III)
  - ✅ agent.md (already updated with token-saving output style)
  - ✅ .specify/templates/spec-template.md (compatible - concise requirements align)
  - ✅ .specify/templates/tasks-template.md (compatible - bullet format aligns)
  - ✅ .specify/templates/agent-file-template.md (compatible)
  - ✅ .specify/templates/checklist-template.md (compatible)
  
  Follow-up TODOs: None
  
  Version Bump Rationale: MINOR 1.1.0 - Material expansion of Principle III from basic
  documentation requirements to comprehensive token-efficiency mandate affecting all output,
  agent behavior, and documentation style. Not backward incompatible (existing docs still
  valid), but adds new guidance that materially changes expectations.
-->

# Vibes Project Constitution

## Core Principles

### I. Skills-First Architecture

Every capability in this repository MUST be packaged as a reusable Skill that can be
loaded and applied across Claude platforms (Claude.ai, Claude Code, API). Skills are
the atomic unit of functionality.

**Non-Negotiable Rules**:
- All new features MUST be delivered as Skills with a SKILL.md file
- Skills MUST be self-contained with clear scope and activation context
- Skills MUST work consistently across Claude.ai, Claude Code, and API contexts
- Skills MUST NOT depend on platform-specific features unless explicitly documented

**Rationale**: Reusability is the core value proposition of this repository. Contributors
and users expect every Skill to work seamlessly regardless of which Claude platform they
use. Platform-specific dependencies fragment the ecosystem and reduce value.

### II. Cross-Platform Compatibility

All Skills, templates, and patterns MUST maintain compatibility across Claude.ai web
interface, Claude Code CLI, and Anthropic API implementations.

**Non-Negotiable Rules**:
- Skills MUST NOT use platform-exclusive syntax or features without graceful degradation
- Templates MUST render correctly in both web and terminal environments
- Documentation MUST specify any platform-specific considerations or limitations
- Examples MUST include invocation patterns for all supported platforms

**Rationale**: Users adopt different Claude platforms based on their workflow. A Skill
that only works in one platform creates fragmentation and limits adoption. Cross-platform
compatibility ensures maximum utility and reach.

### III. Token-Efficient Communication

All documentation, agent output, and Skill instructions MUST minimize token usage through
concise, direct communication with zero fluff or unnecessary elaboration.

**Non-Negotiable Rules**:
- SKILL.md MUST be concise: clear activation context, capabilities, examples only
- Agent responses MUST avoid summaries, preambles, or repeating user input
- Templates MUST include only essential inline guidance
- Output format: results → approval question → done (no explanatory prose)
- Use bullets and code blocks over paragraphs
- README files MUST be scannable with minimal prose

**Rationale**: Token efficiency directly impacts cost, latency, and context window
utilization. Verbose documentation wastes tokens and degrades AI performance. Concise
communication is faster to read, cheaper to process, and easier to maintain.

### IV. Template Consistency

All specification templates (plan, spec, tasks, etc.) MUST maintain consistent structure,
naming conventions, and cross-references to enable reliable AI-assisted workflows.

**Non-Negotiable Rules**:
- Templates MUST use standardized placeholder tokens (e.g., [FEATURE], [DATE])
- File naming MUST follow the pattern: [###-feature-name]/{plan,spec,tasks,...}.md
- Cross-references between templates MUST remain valid across updates
- Template changes MUST be synchronized across all dependent templates

**Rationale**: AI agents rely on consistent structure to parse and generate specifications.
Template inconsistency causes parse failures, incorrect generation, and workflow breakage.
Consistency enables reliable automation.

### V. Incremental Value Delivery

Features and Skill capabilities MUST be designed to deliver value incrementally through
independently testable user stories or workflow stages.

**Non-Negotiable Rules**:
- Specifications MUST break features into prioritized user stories (P1, P2, P3...)
- Each user story MUST be independently implementable and demonstrable
- Task lists MUST organize work by user story to enable incremental delivery
- MVP MUST be clearly identified as the highest priority (P1) user story

**Rationale**: Incremental delivery reduces risk, enables faster feedback, and allows
early validation of assumptions. Monolithic "all-or-nothing" features increase failure
rates and delay value realization.

## Technology Standards

This project is primarily a documentation and specification repository. Technology
standards apply to any implementation examples or tooling:

**Documentation Format**: GitHub-flavored Markdown with CommonMark compatibility  
**Template Engine**: Plain text with bracketed placeholders [TOKEN_NAME]  
**File Organization**: Hierarchical folder structure with README.md navigation  
**Version Control**: Git with semantic versioning for constitution and templates  
**Platform Support**: Claude.ai web + Claude Code CLI + Anthropic API

**Constraints**:
- Skills MUST be plain Markdown without external dependencies
- Templates MUST be parseable by AI agents without special tooling
- Examples MUST NOT require installation beyond Claude platform access

## Quality Gates

Before any Skill or template is considered complete, it MUST pass these gates:

**Gate 1 - Constitution Compliance**
- Verify Skill follows Skills-First Architecture (Principle I)
- Verify cross-platform compatibility or documented limitations (Principle II)
- Verify complete documentation in SKILL.md (Principle III)
- Verify template consistency if applicable (Principle IV)

**Gate 2 - Documentation Quality**
- SKILL.md clearly describes activation context and capabilities
- Examples are executable and demonstrate key use cases
- Edge cases and limitations are explicitly documented
- README is updated to reflect new Skill or template

**Gate 3 - Integration Validation**
- New Skills integrate with existing Skill ecosystem without conflicts
- Template changes are propagated to all dependent templates
- Cross-references between files remain valid
- Repository structure documentation is current

**Gate 4 - User Value Verification**
- Skill delivers clear, measurable value to target users
- Use cases are realistic and represent real-world workflows
- Skill scope is focused and does not overlap with existing Skills
- Contribution aligns with repository's mission and vision

## Governance

This constitution is the authoritative governance document for the Vibes project. All
contributions, reviews, and decisions MUST comply with the principles and standards
defined herein.

**Amendment Process**:
- Proposed amendments MUST be documented in a pull request with rationale
- Amendments MUST specify version bump (MAJOR/MINOR/PATCH) and impact analysis
- MAJOR changes require approval from project maintainers
- All amendments MUST update version metadata and Last Amended date
- Template propagation MUST complete before amendment is merged

**Versioning Policy**:
- MAJOR: Backward incompatible changes to core principles or governance
- MINOR: New principles, sections, or material expansions to guidance
- PATCH: Clarifications, typo fixes, non-semantic refinements

**Compliance Review**:
- All pull requests MUST include a Constitution Compliance checklist
- Maintainers MUST verify compliance before merging contributions
- Violations MUST be documented and justified or corrected
- Repeated violations may result in contribution rejection

**Complexity Justification**:
- Any complexity that appears to violate simplicity principles MUST be justified
- Justifications MUST explain why simpler alternatives are insufficient
- Unjustified complexity is grounds for rejection or refactoring

**Living Document**:
- This constitution evolves with the project's needs
- Regular reviews ensure principles remain relevant and effective
- Community feedback informs amendments and improvements

**Version**: 1.1.0 | **Ratified**: 2026-02-11 | **Last Amended**: 2026-02-12
