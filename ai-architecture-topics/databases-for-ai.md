---
title: "Databases for AI"
summary: "Compare relational databases, vector stores, feature stores, and metadata catalogs in AI systems"
---

# Databases for AI

> Choose the right database technology for each part of your AI stack.

![databases for ai](/img/databases-for-ai.svg)

## TL;DR
- **Relational databases** store structured records and transactional data.
- **Vector stores** index embeddings for similarity search.
- **Feature stores** manage versioned ML features for training and serving.
- **Metadata catalogs** track datasets, models, and lineage.

## Quickstart (Do this now)
1. Start with a relational database for source-of-truth business data.
2. Generate embeddings and load them into a vector store for semantic search.
3. Use a feature store to share validated features between training and inference.
4. Register datasets and models in a metadata catalog for discoverability.

## The Idea (Slightly deeper)
Traditional applications rely on relational databases for consistent transactions and reporting. AI systems add new storage needs:
- **Vector stores** power RAG and recommendation systems by searching high-dimensional embeddings.
- **Feature stores** provide a central hub for engineered features, ensuring training/serving consistency.
- **Metadata catalogs** document datasets, models, and experiments so teams can trace lineage and reuse assets.
These components complement relational systems rather than replace them.

## Diagram
![Databases for AI Diagram](/img/diagrams/databases-for-ai.svg)

## Key Concepts
- **ACID vs. Similarity**: relational DBs guarantee transactions; vector stores focus on nearest neighbor search.
- **Offline vs. Online Features**: feature stores separate batch-generated features from low-latency serving layers.
- **Lineage Tracking**: metadata catalogs record where data comes from and how models were built.

## When to Use This
- **Use when**: Building AI products that mix transactional data with semantic search.
- **Use when**: Multiple teams need consistent features and dataset governance.
- **Don't use when**: A single script or prototype can hard-code features and data sources.
- **Consider alternatives**: Simple object storage or JSON files for small experiments.

## Real-World Examples
- **PostgreSQL**: Reliable relational database with JSON and vector extensions → [PostgreSQL](https://www.postgresql.org/)
- **Pinecone**: Managed vector database for semantic search → [Pinecone](https://www.pinecone.io/)
- **Feast**: Open-source feature store → [Feast](https://feast.dev/)
- **MLflow Model Registry**: Metadata catalog for model tracking → [MLflow](https://mlflow.org/)

## Common Pitfalls
- **Embedding drift**: forgetting to reindex vector stores when models change.
- **Feature skew**: training and serving pipelines calculate features differently.
- **Untracked experiments**: losing lineage by skipping metadata catalogs.

## Deep Dives & "Why it's awesome"
- **[Postgres pgvector Extension](https://github.com/pgvector/pgvector)** - Add vector search to a familiar relational DB.
- **[Feast Architecture](https://docs.feast.dev/)** - How feature stores manage offline and online data.
- **[MLflow Tracking](https://mlflow.org/docs/latest/tracking.html)** - Record experiments and model artifacts.

## Next Steps
- **Learn more**: [Vector Stores & Embeddings](ai-architecture-topics/vector-stores-and-embeddings.md) - Dig into similarity search.
- **Try it**: [Feast Quickstart](https://docs.feast.dev/getting-started/quickstart) - Build your first feature repository.
- **Connect**: [OpenML Metadata](https://www.openml.org/) - Explore community datasets and metadata.

