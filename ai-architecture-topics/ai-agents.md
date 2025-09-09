---
title: "AI Agents"
summary: "Design AI agents with planning algorithms, tool-calling patterns, and human-in-the-loop designs"
---

# AI Agents

> Build agents that plan, call tools, and collaborate with humans.

![ai agents and tools](/img/ai-agents-and-tools.png)

## TL;DR
- **Planning algorithms** help agents break tasks into steps and choose the next action.
- **Tool-calling patterns** allow agents to invoke external APIs or functions for specialized capabilities.
- **Human-in-the-loop designs** keep people in control by requiring approval or feedback for key decisions.

## Quickstart (Do this now)
1. Start with a simple planning method like ReAct or a task graph.
2. Expose functions or APIs the agent can call, describing inputs and outputs.
3. Insert checkpoints where a human can review actions or provide context.
4. Log decisions and results to improve future planning.

## The Idea (Slightly deeper)
Agents extend basic language models with goal-directed behavior. They can plan, use tools, and make decisions, as highlighted in [AI Architecture Patterns](ai-architecture-patterns.md) and described in the repository [README](../README.md).

**Planning algorithms** such as search trees or ReAct let an agent determine the sequence of steps needed to reach a goal.

**Tool-calling patterns** define how an agent interacts with functions and services—passing structured arguments, handling responses, and recovering from errors.

**Human-in-the-loop designs** embed human oversight into the workflow. Agents may request approval before executing high-impact actions or ask for clarification when confidence is low.

## Key Concepts
- **Task Planning**: Strategies like ReAct or hierarchical planning to map tasks into executable steps.
- **Tool Interface**: Contract describing available tools, their parameters, and expected outputs.
- **Human Checkpoints**: Decision points where humans validate or adjust agent actions.
- **Memory & Logging**: Storing past steps to inform future decisions and auditing.

## When to Use This
- **Use when**: Tasks require multiple steps, external resources, or oversight.
- **Don't use when**: A single model response suffices or no human review is available.

## Real-World Examples
- **GitHub Copilot** suggesting code and awaiting developer approval.
- **Customer-support bots** escalating complicated cases to human agents.
- **Workflow assistants** calling APIs to create tickets, send emails, or update records.

## Common Pitfalls
- **Unbounded tool access** leading to unintended actions.
- **Missing human oversight** allowing errors to go unnoticed.
- **Poor planning** causing agents to loop or stall.

## Deep Dives & "Why it's awesome"
- **[LangGraph Documentation](https://langchain-ai.github.io/langgraph/)** - State machines and human-in-the-loop agents.

## Next Steps
- Review the broader context in [AI Architecture Patterns](ai-architecture-patterns.md).
- Explore orchestration options in [Orchestration Frameworks](orchestration-frameworks.md).

