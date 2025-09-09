---
title: "Data Lakes & Marts"
summary: "Understand lakehouse architectures, ETL/ELT pipelines, and data governance for AI systems"
---

# Data Lakes & Marts

> Store, transform, and serve data for AI workloads using scalable lakehouse patterns and governed data marts.

![data lakes and data marts](/img/data-lakes-and-data-marts.png)

## TL;DR
- **Data lakes** hold raw, large-scale data in open formats.
- **Data marts** are curated subsets optimized for analytics and ML.
- **Lakehouse** architectures blend the flexibility of lakes with warehouse reliability.
- **Governance** keeps data secure, high-quality, and compliant.

## Quickstart (Do this now)
1. **Ingest** data from sources into a cloud object store (your data lake)
2. **Transform** with ETL/ELT jobs to apply schema, quality checks, and partitions
3. **Publish** governed data marts for BI dashboards or model training
4. **Track lineage** and permissions to ensure trust and compliance

## The Idea (Slightly deeper)
A **lakehouse** combines data lake scalability with warehouse structure. Raw data lands in the lake, then ETL/ELT pipelines refine it into structured tables while preserving history. **Data marts** provide domain-specific views that teams can use without touching the raw lake. Robust **governance**—covering cataloging, quality, access, and retention—prevents data swamps and enables regulated AI use.

## Diagram
![Data Lakes and Marts Flow](/img/diagrams/data-lakes-and-marts.svg)

## Key Concepts
- **Lakehouse storage**: ACID tables on top of low-cost object stores
- **ETL vs ELT**: Transform before or after loading into the lakehouse
- **Data marts**: Curated subsets for analytics or model features
- **Governance**: Metadata catalogs, quality rules, and access controls
- **Lineage**: Tracing data from source to consumption for trust

## When to Use This
- **Use when**: You need one source of truth for both analytics and ML
- **Use when**: Teams require domain-specific slices of enterprise data
- **Don't use when**: A single, small database covers all needs
- **Consider alternatives**: Traditional data warehouses for simpler workloads

## Real-World Examples
- **Delta Lake** on Databricks for lakehouse tables
- **BigQuery** and **Snowflake** for managed lakehouse features
- **Apache Iceberg** or **Hudi** for open table formats

## Common Pitfalls
- **Unmanaged data sprawl** leading to a "data swamp"
- **Missing governance** causing security or compliance issues
- **Slow pipelines** from overcomplicated ETL/ELT jobs
- **Duplicated data marts** without clear ownership

## Deep Dives & "Why it's awesome"
- **[Delta Lake](https://delta.io/)** - Adds reliability and ACID compliance to data lakes
- **[BigQuery Lakehouse](https://cloud.google.com/bigquery/docs/introduction)** - Serverless lakehouse with built-in governance
- **[Snowflake](https://www.snowflake.com/en/data-lake/)** - Cloud data platform supporting lakehouse patterns
- **[Apache Iceberg](https://iceberg.apache.org/)** - Open table format with schema evolution and time travel
- **[Data Mesh](https://martinfowler.com/articles/data-mesh-principles.html)** - Decentralized governance for domain data products

## Next Steps
- **Learn more**: [Evaluation & Observability](evaluation-and-observability.md) - Monitor data quality and pipeline health
- **Try it**: Build a simple lakehouse using Delta Lake and a cloud object store
- **Connect**: Explore [awesome data engineering](https://github.com/igorbarinov/awesome-data-engineering) resources

