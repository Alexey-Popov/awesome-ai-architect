---
title: "Genetic Memory"
summary: "Combine vector stores, knowledge graphs, and retention policies for adaptive agent memory"
---

# Genetic Memory

> Design memory systems for AI agents that evolve over time and stay relevant.

![genetic memory](/img/genetic-memory.png)

## TL;DR
- **Vector-based memory** stores experiences as embeddings so agents can recall similar situations quickly.
- **Knowledge graph integration** links memories to structured entities and relationships for richer reasoning.
- **Retention policies** decide what to keep, compress, or forget so memory stays useful and affordable.

## Quickstart (Do this now)
1. **Capture interactions**: Convert conversations or events into embeddings and store them in a vector database.
2. **Link to a graph**: Connect each memory to entities and relationships in a knowledge graph like Neo4j.
3. **Define retention rules**: Keep recent or high-value memories, archive or delete the rest on a schedule.
4. **Retrieve by context**: Use similarity search plus graph traversal to fetch relevant memories during planning.
5. **Review periodically**: Prune stale data and regenerate embeddings as models or schemas evolve.

## The Idea (Slightly deeper)
Vector memory lets agents recall by meaning, while knowledge graphs provide structured context. Combining them gives both fuzzy recall and precise reasoning. Retention policies prevent unbounded growth by applying heuristics like time-to-live, relevance scoring, or summarization.

## Key Concepts
- **Vector-Based Memory**: Embedding-driven store that retrieves semantically similar past interactions.
- **Knowledge Graph Integration**: Mapping memories to entities/relations so agents can reason over connected facts.
- **Retention Policies**: Rules for pruning, summarizing, or archiving memories to control cost and relevance.

## When to Use This
- **Use when**: Building agents that learn from ongoing interactions and need long-term context.
- **Use when**: You require both semantic recall and explicit reasoning over entities.
- **Don't use when**: A simple stateless chatbot is sufficient.
- **Consider alternatives**: Session-based memory or fixed context windows for short-lived assistants.

## Real-World Examples
- **MemGPT** combines vector stores with summarization to maintain a growing memory.
- **LangChain** offers memory modules that hook into knowledge graphs and vector databases.
- **Custom agents** storing conversation vectors in Pinecone and facts in Neo4j with scheduled pruning jobs.

## Common Pitfalls
- **Unbounded growth**: Without retention, memory size and costs explode.
- **Stale knowledge**: Memories can become outdated—revalidate or summarize periodically.
- **Privacy leaks**: Sensitive data may persist; apply encryption and deletion policies.

## Next Steps
- **Learn more**: [Vector Stores & Embeddings](vector-stores-and-embeddings.md) – foundations of vector-based recall
- **Explore**: [AI Architecture Patterns](ai-architecture-patterns.md) – how memory fits into larger systems
- **Connect**: [Safety & Security](safety-and-security.md) – policies for handling sensitive memories

