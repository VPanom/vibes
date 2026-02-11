# Repository Architecture

This document provides an overview of how this repository is structured and how the different components work together.

## Design Philosophy

This repository follows these core principles:

1. **Modularity**: Each component (Skills, agents, templates) is self-contained and reusable
2. **Documentation-First**: Every section has comprehensive documentation
3. **Progressive Complexity**: Start simple, add complexity only when needed
4. **Real-World Focus**: Patterns and practices drawn from production experience
5. **Interoperability**: Components work together and with external tools

## Repository Structure

```
vibes/
├── skills/                 # Reusable Claude Skills
├── agents/                 # Agent patterns and implementations
├── templates/              # Specification templates
├── docs/                  # Documentation and best practices
├── ARCHITECTURE.md        # This file
├── README.md              # Repository overview
└── LICENSE                # MIT License
```

## Component Relationships

### Skills Layer
Skills teach Claude how to work according to specific standards and procedures.

**Relationships:**
- Skills reference templates for consistent output
- Skills can trigger agent workflows
- Skills compose with other skills automatically
- Skills work across Claude.ai, Claude Code, and API

**Key Files:**
- `skills/*/SKILL.md` - Skill instructions
- `skills/*/resources/` - Reference materials
- `skills/*/examples/` - Usage examples

### Agent Layer
Agents implement workflow patterns and autonomous systems using Skills.

**Relationships:**
- Agents orchestrate Skills for consistent behavior
- Agents compose multiple Skills dynamically
- Agents follow patterns documented in best practices
- Workflows can be composed into more complex agents

**Key Files:**
- `agents/workflows/` - Predefined patterns
- `agents/autonomous/` - Autonomous implementations
- Agent implementation files with documentation

### Template Layer
Templates provide structured starting points for specifications.

**Relationships:**
- Templates are referenced by spec-generation Skills
- Templates guide agent behavior when creating specs
- Templates ensure consistency across projects
- Templates can be customized per organization

**Key Files:**
- `templates/*/[template-name].md` - Template files
- `templates/*/README.md` - Usage guidance

### Documentation Layer
Centralized knowledge and best practices.

**Relationships:**
- Best practices inform all component development
- Documentation references examples throughout repo
- Guides help users understand relationships
- Evolves based on real-world usage

**Key Files:**
- `docs/best-practices/` - Collected wisdom
- `ARCHITECTURE.md` - This file

## Information Flow

### Development Flow

```
1. Identify Need
   ↓
2. Check Templates/Skills
   ↓
3. Create/Use Specification
   ↓
4. Implement with Agent/Skill
   ↓
5. Test and Refine
   ↓
6. Document Learnings
```

### Skill Application Flow

```
User Query
   ↓
Claude Analyzes Context
   ↓
Identifies Relevant Skills
   ↓
Loads Skill Instructions
   ↓
References Templates/Resources
   ↓
Generates Response
```

### Agent Execution Flow

```
Task Definition
   ↓
Agent Planning (using Skills)
   ↓
Skill Selection and Composition
   ↓
Execution Loop
   ↓
Validation (using Skills/Templates)
   ↓
Result Delivery
```

## Extension Points

### Adding New Skills

1. Create skill directory in appropriate category
2. Write `SKILL.md` with clear instructions
3. Add resources and examples
4. Test with various inputs
5. Document in parent README
6. Consider creating complementary template

### Adding New Agents

1. Choose appropriate category (workflow/autonomous)
2. Implement agent pattern
3. Document workflow and decisions
4. Add usage examples
5. Include testing guidance
6. Reference relevant Skills

### Adding New Templates

1. Identify common specification need
2. Create comprehensive template
3. Include all standard sections
4. Add usage guidance
5. Consider creating Skill to use template
6. Document in category README

## Integration Patterns

### Pattern: Spec-Driven Development

```
Template → Spec Skill → Generated Spec → Implementation Skill → Code → Validation
```

**Components used:**
- Templates (structure)
- Spec-generator Skill (creation)
- Implementation Skills (coding)
- Validation Skills (review)

### Pattern: Agent Workflow

```
Task → Agent Skill → Workflow Pattern → Skill Composition → Validation Skill → Result
```

**Components used:**
- Agent Skills (orchestration)
- Workflow patterns (structure)
- Skill composition (capabilities)
- Validation Skills (quality)

### Pattern: Research and Documentation

```
Query → Research Agent → Analysis Skill → Synthesis Skill → Template → Document
```

**Components used:**
- Research agent pattern
- Analysis Skills
- Synthesis Skills
- Documentation templates

## Versioning Strategy

### Skills
- Semantic versioning in SKILL.md header
- Breaking changes increment major version
- New features increment minor version
- Fixes increment patch version

### Templates
- Version noted in template header
- Change log in template file
- Backward compatibility maintained when possible
- Migration guides for breaking changes

### Agents
- Version in implementation file
- Document workflow changes
- Note Skill dependencies

## Testing Strategy

### Skills Testing
- Test with varied inputs
- Verify template usage
- Check keyword triggering
- Validate composition with other skills

### Agent Testing
- Unit test individual components
- Integration test full workflows
- Test error handling
- Performance benchmarking

### Template Testing
- Use in real projects
- Validate completeness
- Check clarity
- Test with Skills

## Maintenance

### Regular Reviews
- Quarterly review of all components
- Update based on new Claude capabilities
- Incorporate user feedback
- Archive outdated components

### Documentation Updates
- Keep examples current
- Update best practices
- Maintain change logs
- Cross-reference related components

### Dependency Management
- Note Claude API changes
- Update integration patterns
- Test Skills with new features
- Maintain compatibility

## Contributing Guidelines

### Adding Components
1. Follow established patterns
2. Include comprehensive documentation
3. Test thoroughly
4. Update relevant READMEs
5. Maintain consistency with existing code

### Modifying Existing Components
1. Check for dependent components
2. Maintain backward compatibility when possible
3. Document breaking changes
4. Update related documentation
5. Add migration guidance

### Documentation Standards
- Use clear, professional language
- Include concrete examples
- Document edge cases
- Keep up to date
- Cross-reference related sections

## Future Directions

### Planned Enhancements
- Extended thinking integration patterns
- Multi-modal workflow examples
- Advanced agent memory patterns
- Organization-specific skill variants
- Industry-specific template collections

### Research Areas
- Optimal skill composition strategies
- Cost optimization techniques
- Advanced error recovery patterns
- Cross-agent communication
- Long-running workflow management

## Resources

### Internal
- README files throughout repository
- GETTING_STARTED.md for new users
- Best practices documentation
- Example implementations

### External
- [Anthropic Documentation](https://docs.anthropic.com/)
- [Building Effective Agents](https://www.anthropic.com/research/building-effective-agents)
- [Claude Skills Guide](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/overview)
