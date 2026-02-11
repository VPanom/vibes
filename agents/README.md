# Agents

This directory contains practical implementations of agent patterns and workflows for building AI systems with Claude.

## Overview

Agent systems combine LLMs with tools, memory, and structured decision-making to accomplish complex tasks. This collection focuses on proven patterns from simple workflows to autonomous agents.

## Agent Categories

### Workflows
Pre-defined patterns where LLMs and tools are orchestrated through structured code paths.

**When to use workflows:**
- Task has well-defined steps
- Predictability is important
- You can anticipate the path to completion
- Lower latency and cost are priorities

**Common workflow patterns:**
- Prompt Chaining
- Routing
- Parallelization
- Orchestrator-Workers
- Evaluator-Optimizer

### Autonomous
Systems where LLMs dynamically direct their own processes and tool usage.

**When to use autonomous agents:**
- Open-ended problems
- Unpredictable number of steps
- Complex decision trees
- Need for adaptive behavior
- Tasks benefit from model judgment

**Key characteristics:**
- Dynamic tool selection
- Self-directed planning
- Error recovery
- Iterative refinement
- Environmental feedback loops

## Directory Structure

```
agents/
├── workflows/           # Predefined workflow patterns
│   ├── prompt-chaining/
│   ├── routing/
│   ├── parallelization/
│   ├── orchestrator-workers/
│   └── evaluator-optimizer/
└── autonomous/          # Autonomous agent implementations
    ├── research-agent/
    ├── coding-agent/
    └── task-agent/
```

## Workflow Patterns

### 1. Prompt Chaining

Decompose tasks into sequential steps where each LLM call processes the previous output.

**Use cases:**
- Document generation with review
- Multi-stage data transformation
- Translation with quality checks
- Content creation pipelines

**Structure:**
```
Input → Step 1 → Gate Check → Step 2 → Gate Check → Output
```

### 2. Routing

Classify input and direct to specialized handlers.

**Use cases:**
- Customer support triage
- Multi-domain question answering
- Model selection (route to appropriate Claude version)
- Content moderation

**Structure:**
```
Input → Classifier → Route to appropriate handler → Output
```

### 3. Parallelization

Run multiple LLM tasks simultaneously and aggregate results.

**Variants:**
- **Sectioning**: Different subtasks in parallel
- **Voting**: Same task multiple times for consensus

**Use cases:**
- Multi-aspect analysis
- Guardrails (content + safety checks)
- Ensemble evaluations
- Code review from multiple perspectives

### 4. Orchestrator-Workers

Central LLM dynamically breaks down tasks and delegates to worker LLMs.

**Use cases:**
- Complex coding tasks
- Research projects
- Content generation at scale
- Multi-file modifications

**Structure:**
```
Orchestrator → Plan → Delegate to workers → Synthesize results
```

### 5. Evaluator-Optimizer

One LLM generates, another evaluates and provides feedback in a loop.

**Use cases:**
- Literary translation
- Complex research requiring iteration
- High-quality content creation
- Solution refinement

**Structure:**
```
Generator → Output → Evaluator → Feedback → Generator (loop)
```

## Building Effective Agents

### Core Principles

1. **Simplicity First**: Start with the simplest solution that could work
2. **Explicit Planning**: Make the agent's reasoning visible
3. **Clear Interfaces**: Document tools thoroughly (ACI - Agent Computer Interface)

### Essential Components

**1. Environment Feedback**
Agents need "ground truth" at each step:
- Tool execution results
- Code execution output
- API responses
- File system state

**2. Stopping Conditions**
Prevent infinite loops:
- Maximum iterations
- Time limits
- Success criteria
- Error thresholds

**3. Human Checkpoints**
Strategic intervention points:
- Major decisions
- Ambiguous situations
- Error recovery
- Final review

**4. Tool Documentation**
Invest heavily in clear tool definitions:
- Describe purpose and behavior
- Include usage examples
- Document edge cases
- Show expected input/output formats

### Error Handling

**Recovery Strategies:**
- Retry with modified approach
- Escalate to human
- Fall back to simpler method
- Log and continue
- Graceful degradation

**Prevention:**
- Input validation
- Output verification
- State management
- Checkpoint saves
- Rollback capability

## Implementation Guidelines

### Start Simple

```
Level 1: Single LLM call with tools
Level 2: Prompt chaining (2-3 steps)
Level 3: Routing or parallelization
Level 4: Orchestrator-workers
Level 5: Autonomous agent
```

Add complexity only when simpler approaches fail.

### Measure Performance

Track key metrics:
- Task completion rate
- Average iterations
- Cost per task
- Latency
- Error frequency

### Testing Strategy

**Development:**
- Test in sandboxed environments
- Use test data sets
- Monitor resource usage
- Log all decisions

**Production:**
- Gradual rollout
- A/B testing
- User feedback loops
- Continuous monitoring

## Tool Development

Tools are critical for agent success. Follow these guidelines:

### Tool Design Principles

1. **Think Like the Model**: What format is easiest for an LLM?
2. **Minimize Overhead**: Avoid complex formatting requirements
3. **Clear Documentation**: Write excellent "docstrings"
4. **Error Messages**: Provide actionable feedback
5. **Idempotency**: Make operations safe to retry

### Tool Documentation Template

```json
{
  "name": "tool_name",
  "description": "Clear, concise description of what this tool does",
  "parameters": {
    "param1": {
      "type": "string",
      "description": "What this parameter does, expected format, examples"
    }
  },
  "returns": "Description of return value and format",
  "errors": "Common errors and how to handle them",
  "examples": [
    {
      "input": "...",
      "output": "..."
    }
  ]
}
```

## Agent Architectures

### Research Agent

**Purpose**: Gather and synthesize information from multiple sources

**Flow:**
1. Decompose question into research areas
2. Search each area in parallel
3. Evaluate relevance of findings
4. Synthesize coherent answer
5. Iterate if gaps remain

### Coding Agent

**Purpose**: Implement features across multiple files

**Flow:**
1. Analyze requirements
2. Plan file structure
3. Implement changes incrementally
4. Test after each change
5. Refine based on test results

### Task Agent

**Purpose**: Execute multi-step tasks with tool use

**Flow:**
1. Understand goal
2. Plan approach
3. Execute step with tools
4. Verify result
5. Adapt plan if needed
6. Continue until complete

## Best Practices

### Do's

- Start with workflows before building autonomous agents
- Invest time in tool documentation
- Make agent reasoning visible
- Implement comprehensive logging
- Test extensively in safe environments
- Set clear stopping conditions
- Include human oversight for critical decisions

### Don'ts

- Don't use agents for simple tasks
- Don't skip error handling
- Don't assume perfect tool use
- Don't ignore cost implications
- Don't deploy without testing
- Don't create overly complex systems
- Don't forget about latency

## Production Considerations

### Reliability

- Implement retries with backoff
- Handle API failures gracefully
- Validate all tool outputs
- Monitor for drift
- Version control prompts and tools

### Security

- Sandbox agent execution
- Validate all inputs
- Limit tool capabilities
- Audit agent actions
- Implement access controls

### Cost Management

- Set budget limits
- Monitor token usage
- Cache where possible
- Use appropriate models (Haiku vs Sonnet vs Opus)
- Implement early stopping

### Observability

- Log all decisions
- Track tool usage
- Monitor performance metrics
- Alert on anomalies
- Collect user feedback

## Examples

Each subdirectory contains:
- Complete implementation
- Documentation
- Test cases
- Usage examples
- Performance notes

See individual pattern directories for detailed examples.

## Resources

- [Anthropic: Building Effective Agents](https://www.anthropic.com/research/building-effective-agents)
- [Tool Use Documentation](https://docs.anthropic.com/en/docs/build-with-claude/tool-use)
- [Prompt Engineering Guide](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering)
- [Computer Use Documentation](https://docs.anthropic.com/en/docs/build-with-claude/computer-use)

## Contributing

When adding agent implementations:

1. Include complete documentation
2. Provide working examples
3. Document performance characteristics
4. Include test cases
5. Note limitations and edge cases
6. Follow established patterns
