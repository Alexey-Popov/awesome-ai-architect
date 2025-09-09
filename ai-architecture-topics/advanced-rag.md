---
title: "Advanced RAG"
summary: "Boost retrieval-augmented generation accuracy with reranking, multi-hop search, and feedback loops"
---

# Advanced RAG

> Build RAG systems that move beyond basic vector search using retrieval pipelines, re-rankers, and iterative generation.

![Advanced RAG](/img/advanced-rag-patterns.png)

## TL;DR
- **Hybrid retrieval** combines vector search (semantic) with keyword search (exact matches) for 15-25% better accuracy
- **Reranking** improves precision by 20-40% but adds 50-200ms latency
- **Multi-hop retrieval** enables complex reasoning but increases costs by 2-3x
- **Caching** reduces costs by 60-80% for repeated queries

## Quickstart (Do this now)
1. **Start with hybrid search**: Combine vector + keyword search for better recall
2. **Add reranking**: Use cross-encoder models like BGE-reranker for precision
3. **Implement caching**: Cache embeddings and final responses to reduce costs
4. **Test multi-hop**: Build query chains for complex information gathering
5. **Measure everything**: Track accuracy, latency, and costs with each change

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

## Cost & Performance Metrics

### Retrieval Performance
| Method | Accuracy | Latency | Cost/Query | Use Case |
|--------|----------|---------|------------|----------|
| Vector Search | 70-80% | 50-100ms | $0.001-0.005 | General semantic search |
| Hybrid Search | 80-90% | 80-150ms | $0.002-0.008 | Balanced accuracy/speed |
| Reranked Search | 85-95% | 150-300ms | $0.005-0.015 | High precision needed |
| Multi-hop | 90-98% | 500-2000ms | $0.010-0.050 | Complex reasoning |

### Caching Impact
- **Embedding Cache**: 60-80% cost reduction for repeated queries
- **Response Cache**: 90%+ cost reduction for identical questions
- **Chunk Cache**: 40-60% cost reduction for document processing

## Decision Tree: Which RAG Pattern to Use?

```
Start: Building a RAG system
│
├─ Is accuracy more important than speed?
│  ├─ YES → Is budget flexible?
│  │  ├─ YES → Use Multi-hop + Reranking (90-98% accuracy, $0.01-0.05/query)
│  │  └─ NO → Use Hybrid + Reranking (85-95% accuracy, $0.005-0.015/query)
│  └─ NO → Is this a new system?
│     ├─ YES → Start with Vector Search (70-80% accuracy, $0.001-0.005/query)
│     └─ NO → Use Hybrid Search (80-90% accuracy, $0.002-0.008/query)
│
├─ Do you have repeated queries?
│  ├─ YES → Implement caching (60-90% cost reduction)
│  └─ NO → Skip caching initially
│
└─ Do you need real-time updates?
   ├─ YES → Use streaming retrieval + incremental indexing
   └─ NO → Use batch processing + periodic reindexing
```

## When to Use
- **Vector Search**: General semantic search, prototyping, low-latency requirements
- **Hybrid Search**: Production systems needing balanced accuracy/speed
- **Reranking**: High-precision applications, legal/medical domains
- **Multi-hop**: Complex reasoning, research assistants, citation tracking
- **Caching**: High-traffic systems, repeated queries, cost optimization

## Implementation Checklist

### Phase 1: Foundation 
- [ ] **Data Preparation**
  - [ ] Document chunking strategy defined (500-1000 chars with overlap)
  - [ ] Metadata schema designed (source, date, type, etc.)
  - [ ] Quality control process for data cleaning
- [ ] **Basic Retrieval**
  - [ ] Vector database selected and configured
  - [ ] Embedding model chosen and tested
  - [ ] Similarity threshold tuned (start with 0.7)
  - [ ] Basic evaluation metrics implemented

### Phase 2: Enhancement 
- [ ] **Hybrid Search**
  - [ ] Keyword search integrated (BM25 or similar)
  - [ ] Fusion algorithm implemented (RRF, weighted)
  - [ ] Performance benchmarked vs vector-only
- [ ] **Reranking**
  - [ ] Cross-encoder model selected (BGE-reranker, Cohere)
  - [ ] Reranking pipeline implemented
  - [ ] Top-k retrieval optimized (20-50 → 5-10)
  - [ ] Latency impact measured

### Phase 3: Optimization 
- [ ] **Caching Strategy**
  - [ ] Embedding cache implemented (Redis/Memcached)
  - [ ] Response cache for identical queries
  - [ ] Cache invalidation strategy defined
  - [ ] Cache hit rate monitoring
- [ ] **Multi-hop (if needed)**
  - [ ] Query decomposition logic
  - [ ] Intermediate result storage
  - [ ] Chain-of-thought prompting
  - [ ] Cost monitoring for multiple LLM calls

### Phase 4: Production 
- [ ] **Monitoring & Observability**
  - [ ] Query latency tracking
  - [ ] Accuracy metrics dashboard
  - [ ] Cost per query monitoring
  - [ ] Error rate and fallback handling
- [ ] **Performance Tuning**
  - [ ] Load testing completed
  - [ ] Auto-scaling configured
  - [ ] Circuit breakers implemented
  - [ ] A/B testing framework ready

## Examples
- [ColBERT](https://github.com/stanford-futuredata/ColBERT) – efficient late interaction reranker for search.
- [LlamaIndex RAG pipeline](https://github.com/run-llama/llama_index) – modular retrieval chains with query transforms.
- [OpenAI function calling with retrieval](https://platform.openai.com/docs/guides/function-calling) – letting models decide follow-up searches.

## Pitfalls
- Ignoring relevance scores can lead to hallucinated answers.
- Overly small chunks break context; overly large chunks waste tokens.
- Complex pipelines increase latency and maintenance overhead.

## Deep Dives & Why

### Implementation Guides
- **[Pinecone Hybrid Search Guide](https://www.pinecone.io/learn/hybrid-search/)** - Production-ready hybrid search with code examples and performance tuning
- **[Weaviate Hybrid Search Tutorial](https://weaviate.io/developers/weaviate/search/hybrid)** - Step-by-step implementation with real datasets

### Tools & Frameworks
- **[Haystack RAG Pipeline](https://docs.haystack.deepset.ai/docs/pipelines)** - Enterprise-grade RAG framework with built-in evaluation
- **[LangGraph Multi-Agent RAG](https://langchain-ai.github.io/langgraph/concepts/multi_agent/)** - Multi-agent systems for complex information gathering

### Cost Optimization
- **[Vector Database Cost Comparison](https://zilliz.com/comparison)** - Detailed cost analysis across different vector databases

## Next Steps
- **Explore**: [Vector Stores & Embeddings](ai-architecture-topics/vector-stores-and-embeddings.md) for better indexing.
- **Orchestrate**: [Orchestration Frameworks](ai-architecture-topics/orchestration-frameworks.md) to manage multi-step retrieval.
- **Evaluate**: [Evaluation & Observability](ai-architecture-topics/evaluation-and-observability.md) to measure quality.

