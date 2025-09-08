---
title: "Advanced RAG"
summary: "Boost retrieval-augmented generation accuracy with reranking, multi-hop search, and feedback loops"
---

# Advanced RAG

> Build RAG systems that move beyond basic vector search using retrieval pipelines, re-rankers, and iterative generation.

![Advanced RAG](/img/advanced-rag.svg)

## TL;DR
- RAG quality improves when you combine vector search with keyword filters and reranking.
- Better chunking and multi-hop retrieval reduce hallucinations.
- Feedback loops and caching keep responses fast and up to date.

## Quickstart (Do this now)
1. Index your data with both embeddings and keywords.
2. Add a reranker model to score retrieved passages.
3. Test multi-step retrieval where one answer triggers another search.
4. Cache final responses and frequently used chunks.
5. Evaluate results with a human-reviewed dataset.

## The Idea (Slightly deeper)
Basic RAG fetches a few documents and feeds them to a model. Advanced RAG adds extra retrieval steps, re-ranks results, and uses query transformations to find better context. By chaining retrieval and generation, the system can research topics, follow citations, or summarize large corpora.

## Diagram
![Advanced RAG Flow](/img/diagrams/advanced-rag-flow.svg)

## Key Concepts
- **Query Expansion** – reformulate the question with synonyms or follow-up prompts.
- **Hybrid Search** – combine dense embeddings with traditional keyword filters.
- **Reranking** – use a cross-encoder model to score and reorder retrieved chunks.
- **Multi-Hop Retrieval** – run successive searches to traverse related documents.
- **Caching** – store useful chunks or final answers to avoid repeated work.

## When to Use
- When answers require up-to-date or domain-specific knowledge.
- When basic RAG returns irrelevant or low-quality context.
- When building assistants that must cite sources or drill into documents.
- Avoid when a static knowledge base is sufficient or latency is critical.

## Examples
- [ColBERT](https://github.com/stanford-futuredata/ColBERT) – efficient late interaction reranker for search.
- [LlamaIndex RAG pipeline](https://github.com/run-llama/llama_index) – modular retrieval chains with query transforms.
- [OpenAI function calling with retrieval](https://platform.openai.com/docs/guides/function-calling) – letting models decide follow-up searches.

## Pitfalls
- Ignoring relevance scores can lead to hallucinated answers.
- Overly small chunks break context; overly large chunks waste tokens.
- Complex pipelines increase latency and maintenance overhead.

## Deep Dives
- [RAG triad: retrieval, reranking, generation](https://arxiv.org/abs/2402.19433)
- [Hybrid search guide](https://www.pinecone.io/learn/hybrid-search/)
- [Feedback loops for RAG](https://docs.langchain.com/docs/use_cases/toolkits/self-query/)

## Next Steps
- **Explore**: [Vector Stores & Embeddings](ai-architecture-topics/vector-stores-and-embeddings.md) for better indexing.
- **Orchestrate**: [Orchestration Frameworks](ai-architecture-topics/orchestration-frameworks.md) to manage multi-step retrieval.
- **Evaluate**: [Evaluation & Observability](ai-architecture-topics/evaluation-and-observability.md) to measure quality.

