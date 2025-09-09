---
title: "Databases for AI"
summary: "Compare relational databases, vector stores, feature stores, and metadata catalogs in AI systems"
---

# Databases for AI

> Choose the right database technology for each part of your AI stack.

![databases for ai](/img/db-for-ai.png)

## TL;DR
- **Relational databases** store structured records and transactional data (ACID compliance, 1-10ms queries).
- **Vector stores** index embeddings for similarity search (50-200ms for 1M+ vectors).
- **Feature stores** manage versioned ML features for training and serving (10-100ms feature retrieval).
- **Metadata catalogs** track datasets, models, and lineage (enables data governance and compliance).

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

## Database Performance & Cost Comparison

### Relational Databases
| Database | Query Latency | Throughput | Cost/Month | Best For |
|----------|---------------|------------|------------|----------|
| PostgreSQL | 1-5ms | 10K-100K QPS | $50-500 | General purpose, ACID |
| MySQL | 1-3ms | 20K-200K QPS | $30-300 | High throughput |
| SQLite | 0.1-1ms | 1K-10K QPS | $0 | Development, embedded |
| CockroachDB | 2-10ms | 5K-50K QPS | $100-1000 | Distributed, global |

### Vector Stores
| Database | Query Latency | Vectors Supported | Cost/Month | Best For |
|----------|---------------|-------------------|------------|----------|
| Pinecone | 50-100ms | 1M-1B+ | $70-700 | Managed, scalable |
| Weaviate | 20-80ms | 1M-100M | $0-500 | Open source, flexible |
| Chroma | 10-50ms | 1K-10M | $0-100 | Development, simple |
| Qdrant | 30-100ms | 1M-1B+ | $0-300 | Self-hosted, fast |

### Feature Stores
| Platform | Feature Retrieval | Throughput | Cost/Month | Best For |
|----------|-------------------|------------|------------|----------|
| Feast | 10-50ms | 1K-10K QPS | $0-200 | Open source, flexible |
| Tecton | 5-20ms | 10K-100K QPS | $500-5000 | Enterprise, managed |
| Hopsworks | 20-100ms | 1K-5K QPS | $200-2000 | Full ML platform |
| AWS Feature Store | 10-30ms | 5K-50K QPS | $100-1000 | AWS ecosystem |

### Metadata Catalogs
| Platform | Search Latency | Storage | Cost/Month | Best For |
|----------|----------------|---------|------------|----------|
| MLflow | 100-500ms | 1GB-1TB | $0-100 | Model tracking |
| DataHub | 200-1000ms | 10GB-10TB | $0-500 | Data lineage |
| Apache Atlas | 500-2000ms | 100GB-100TB | $0-1000 | Enterprise governance |
| AWS Glue | 100-300ms | 1TB-100TB | $200-2000 | AWS ecosystem |

## Decision Tree: Which Database for AI?

```
Start: Need to store data for AI system
│
├─ What type of data?
│  ├─ Structured records → Relational DB (PostgreSQL, MySQL)
│  ├─ Embeddings/vectors → Vector Store (Pinecone, Weaviate)
│  ├─ ML features → Feature Store (Feast, Tecton)
│  └─ Metadata/lineage → Metadata Catalog (MLflow, DataHub)
│
├─ What's your scale?
│  ├─ < 1M records → SQLite, Chroma (simple)
│  ├─ 1M-100M records → PostgreSQL, Weaviate (balanced)
│  └─ > 100M records → CockroachDB, Pinecone (distributed)
│
├─ What's your latency requirement?
│  ├─ < 10ms → Relational DB or Feature Store
│  ├─ 10-100ms → Vector Store or managed services
│  └─ > 100ms → Metadata Catalog (batch processing)
│
└─ What's your budget?
   ├─ < $100/month → Open source (PostgreSQL, Feast, MLflow)
   ├─ $100-1000/month → Managed services (Pinecone, Tecton)
   └─ > $1000/month → Enterprise platforms (AWS, enterprise features)
```

## When to Use This
- **Relational DBs**: Transactional data, user records, business logic, ACID compliance needed
- **Vector Stores**: Semantic search, RAG systems, recommendation engines, similarity matching
- **Feature Stores**: ML training/serving consistency, feature sharing across teams
- **Metadata Catalogs**: Data governance, model tracking, compliance, lineage requirements

## Real-World Examples
- **PostgreSQL**: Reliable relational database with JSON and vector extensions → [PostgreSQL](https://www.postgresql.org/)
- **Pinecone**: Managed vector database for semantic search → [Pinecone](https://www.pinecone.io/)
- **Feast**: Open-source feature store → [Feast](https://feast.dev/)
- **MLflow Model Registry**: Metadata catalog for model tracking → [MLflow](https://mlflow.org/)

## Implementation Checklist

### Phase 1: Foundation
- [ ] **Relational Database Setup**
  - [ ] Choose database (PostgreSQL for most cases)
  - [ ] Design schema for business data
  - [ ] Set up connection pooling
  - [ ] Configure backups and monitoring
- [ ] **Basic Data Pipeline**
  - [ ] Set up data ingestion from sources
  - [ ] Implement data validation and cleaning
  - [ ] Create data quality checks
  - [ ] Document data schemas

### Phase 2: Vector Search
- [ ] **Vector Store Implementation**
  - [ ] Choose vector database (Pinecone for managed, Weaviate for open source)
  - [ ] Generate embeddings for existing data
  - [ ] Set up vector indexing and search
  - [ ] Implement similarity search APIs
- [ ] **RAG Integration**
  - [ ] Connect vector store to LLM
  - [ ] Implement retrieval and generation pipeline
  - [ ] Add metadata filtering
  - [ ] Test search quality and performance

### Phase 3: Feature Management
- [ ] **Feature Store Setup**
  - [ ] Choose feature store (Feast for open source, Tecton for enterprise)
  - [ ] Define feature schemas and transformations
  - [ ] Set up offline feature computation
  - [ ] Implement online feature serving
- [ ] **ML Pipeline Integration**
  - [ ] Connect features to training pipelines
  - [ ] Implement feature validation
  - [ ] Set up feature monitoring
  - [ ] Add feature versioning

### Phase 4: Metadata & Governance
- [ ] **Metadata Catalog**
  - [ ] Choose catalog (MLflow for models, DataHub for data)
  - [ ] Set up data lineage tracking
  - [ ] Implement model registry
  - [ ] Add experiment tracking
- [ ] **Data Governance**
  - [ ] Set up access controls
  - [ ] Implement data quality monitoring
  - [ ] Add compliance reporting
  - [ ] Create data documentation

## Common Pitfalls
- **Embedding drift**: forgetting to reindex vector stores when models change
- **Feature skew**: training and serving pipelines calculate features differently
- **Untracked experiments**: losing lineage by skipping metadata catalogs
- **Over-engineering**: using complex databases when simple ones suffice
- **No monitoring**: missing performance issues and data quality problems

## Deep Dives & "Why it's awesome"

### Relational Databases
- **[PostgreSQL pgvector](https://github.com/pgvector/pgvector)** - Add vector search capabilities to PostgreSQL
- **[MySQL Performance Tuning](https://dev.mysql.com/doc/refman/8.0/en/optimization.html)** - Official MySQL optimization guide
- **[CockroachDB Architecture](https://www.cockroachlabs.com/docs/stable/architecture/overview.html)** - Distributed SQL database design

### Vector Stores
- **[Pinecone Documentation](https://docs.pinecone.io/)** - Managed vector database with automatic scaling
- **[Weaviate Vector Search Guide](https://weaviate.io/developers/weaviate/current/vector-db/vector-search.html)** - Open-source vector database implementation
- **[Qdrant Performance Guide](https://qdrant.tech/documentation/guides/performance/)** - High-performance vector search optimization

### Feature Stores
- **[Feast Architecture](https://docs.feast.dev/concepts/architecture/)** - How feature stores manage offline and online data
- **[Tecton Feature Store](https://docs.tecton.ai/)** - Enterprise-grade feature platform
- **[Hopsworks Feature Store](https://docs.hopsworks.ai/feature-store/)** - Full ML platform with feature management

### Metadata & Governance
- **[MLflow Model Registry](https://mlflow.org/docs/latest/model-registry.html)** - Model versioning and lifecycle management
- **[DataHub Architecture](https://datahubproject.io/docs/architecture/)** - LinkedIn's data discovery and lineage platform
- **[Apache Atlas Documentation](https://atlas.apache.org/)** - Enterprise data governance and metadata management

### Database Comparison Tools
- **[DB-Engines Ranking](https://db-engines.com/en/ranking)** - Database popularity and feature comparison
- **[Vector Database Comparison](https://zilliz.com/comparison)** - Detailed comparison of vector database options
- **[Feature Store Comparison](https://www.featurestore.org/)** - Comprehensive feature store evaluation

## Next Steps
- **Learn more**: [Vector Stores & Embeddings](ai-architecture-topics/vector-stores-and-embeddings.md) - Dig into similarity search.
- **Try it**: [Feast Quickstart](https://docs.feast.dev/getting-started/quickstart) - Build your first feature repository.
- **Connect**: [OpenML Metadata](https://www.openml.org/) - Explore community datasets and metadata.

