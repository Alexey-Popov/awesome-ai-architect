# Awesome AI Architect

> 10x your AI Architect journey with plain‑language, hands‑on guides that blend AI engineering and solution architecture.

![awesome-ai-architect](img/awesome-ai-architect-kb.png)

## 📚 Table of Contents

### 🏗️ Core Topics
- [AI Architecture Patterns](ai-architecture-topics/ai-architecture-patterns.md) - RAG, agents, pipelines, and orchestration
- [Vector Stores & Embeddings](ai-architecture-topics/vector-stores-and-embeddings.md) - Storage, retrieval, and similarity search
- [Databases for AI](ai-architecture-topics/databases-for-ai.md) - Relational tables, vector indexes, feature stores, and metadata catalogs
- [Serving & Scaling](ai-architecture-topics/serving-and-scaling.md) - Inference servers, GPUs, and autoscaling
- [Inference Infrastructure](ai-architecture-topics/inference-infrastructure.md) - GPUs, TPUs, quantization, and cost-performance metrics
- [Evaluation & Observability](ai-architecture-topics/evaluation-and-observability.md) - Testing, monitoring, and cost tracking
- [Guardrails](ai-architecture-topics/guardrails.md) - NeMo Guardrails, Rebuff, and custom policy engines
- [Observability](ai-architecture-topics/observability.md) - Prometheus, OpenTelemetry, drift detection, and alerting practices
- [Safety & Security](ai-architecture-topics/safety-and-security.md) - OWASP LLM Top 10, guardrails, and best practices
- [Red Teaming](ai-architecture-topics/red-teaming.md) - Scenario generation, attack simulations, and reporting workflows
- [Security & Compliance](ai-architecture-topics/security-compliance.md) - Regulatory requirements, encryption, and model provenance tracking
- [Orchestration Frameworks](ai-architecture-topics/orchestration-frameworks.md) - LangChain, LangGraph, and workflow tools
- [Code Execution Sandboxes](https://e2b.dev/) - E2B micro-VMs for isolated tool execution and security
- [Advanced RAG](ai-architecture-topics/advanced-rag.md) - Multi-hop retrieval, rerankers, and feedback loops
- [Cloud for AI](ai-architecture-topics/cloud-for-ai.md) - AWS, Azure, and GCP services and best practices
- [Multi-Cloud](ai-architecture-topics/multi-cloud.md) - Portability, data residency, failover, and cost arbitrage
- [Model Routing](ai-architecture-topics/model-routing.md) - Dynamically choose the best model for a task
- [Multi-LLM Strategies](ai-architecture-topics/multi-llm.md) - Voting, specialists, and cost-aware selection
- [Data Scraping](ai-architecture-topics/data-scraping.md) - robots.txt, throttling, and content licensing
- [Data Lakes & Marts](ai-architecture-topics/data-lakes-and-marts.md) - Lakehouse concepts, ETL/ELT pipelines, and governance
- [AI Workflow Automation](ai-architecture-topics/ai-workflow-automation.md) - DAG schedulers and model CI/CD
- [Genetic Memory](ai-architecture-topics/genetic-memory.md) - Vector memory, knowledge graphs, and retention
- [On-Device vs VM](ai-architecture-topics/on-device-vs-vm.md) - Latency, privacy, and hardware trade-offs

### 🛰️ System Design for AI Architects
- [Distributed Systems Foundations](system-design/distributed-systems-foundations.md) - CAP/PACELC, partial failure, and consistency baselines for AI platforms
- [Idempotency, Retries & Delivery Semantics](system-design/idempotency-retries-delivery.md) - Safe LLM and tool retries without duplicate side effects
- [Reliability & Failure Design](system-design/reliability-and-failure-design.md) - Timeouts, breakers, bulkheads, and model/cache/human fallbacks
- [Caching Layers for AI](system-design/caching-for-ai.md) - CDN, response, embedding, retrieval, and model cache layers
- [Rate Limiting & Throughput](system-design/rate-limiting-and-throughput.md) - Token/QPS quotas, fairness, and backpressure for LLM APIs
- [AI Request Path & Gateways](system-design/ai-request-path-and-gateways.md) - Client to edge to gateway to guardrails to router to model
- [Sync, Async & Streaming APIs](system-design/sync-async-streaming-apis.md) - SSE/WebSocket streaming, 202 jobs, and webhooks for long AI work
- [Event-Driven AI Pipelines](system-design/event-driven-ai-pipelines.md) - Ingest, embed refresh, and eval streams with brokers and queues
- [Background Jobs & Durable Workflows](system-design/background-jobs-and-durable-workflows.md) - Agents, batch, and reindex beyond HTTP with durable orchestration
- [Multi-Tenancy for AI Platforms](system-design/multi-tenancy-for-ai.md) - Isolation of indexes, prompts, caches, and models
- [Multi-Region & High Availability](system-design/multi-region-and-ha.md) - GPU scarcity, residency, and failover for global AI
- [AuthN & AuthZ for AI](system-design/authn-authz-for-ai.md) - OAuth/OIDC, agent identity, and fine-grained tool/data auth
- [Data Movement & Lifecycle](system-design/data-movement-and-lifecycle.md) - Ingest, serve, evolve, and delete for AI data planes
- [State & Service Boundaries](system-design/state-and-service-boundaries.md) - Session and agent state placement with modular boundaries
- [Agent & Tool Gateways](system-design/agent-and-tool-gateways.md) - Gated tool access with discovery, policy, quotas, and audit
- [Prompt Caching vs Semantic Caching](system-design/prompt-and-semantic-caching.md) - Prefix reuse vs similarity hits with tenancy-safe keys
- [KV Cache & Memory Cost](system-design/kv-cache-and-memory-cost.md) - KV cache as a concurrency and context capacity constraint
- [LLM Efficiency Techniques](system-design/llm-efficiency-techniques.md) - Quantization, distillation, batching, caching, routing, speculative decoding
- [Speculative Decoding & Serving Engines](system-design/speculative-decoding-and-serving-engines.md) - Draft/verify pattern and serving engine choice
- [Context Engineering as Architecture](system-design/context-engineering-as-architecture.md) - Context window as a budgeted, governed resource
- [Agent Memory Architecture](system-design/agent-memory-architecture.md) - Short, long, episodic, and semantic memory with forget policies
- [Agent Loop & Harness](system-design/agent-loop-and-harness.md) - Planner/executor runtime, budgets, and human-in-the-loop checkpoints
- [Multi-Agent & Agent Protocols](system-design/multi-agent-and-agent-protocols.md) - Orchestrator vs peer topologies and protocol roles
- [Skills vs MCP vs RAG Capability Layers](system-design/skills-mcp-rag-capability-layers.md) - Decision matrix for extending models
- [Model Customization Decision](system-design/model-customization-decision.md) - Prompt, RAG, fine-tune, and LoRA decision tree
- [Eval Recipes & LLM-as-Judge](system-design/eval-recipes-and-llm-judge.md) - Offline and online eval pipelines as architecture components
- [AI Cost & Token Economics](system-design/ai-cost-and-token-economics.md) - Unit economics, routing, showback, and chargeback
- [Realtime & Multimodal AI Architecture](system-design/realtime-and-multimodal-ai-architecture.md) - Voice, streaming transports, and multimodal ingest

### 💻 AI for Software Engineering Skills

- [MySpec](https://myspec.dev) — Spec-driven development platform compiling guided developer discovery interviews into deterministic 4-file specification bundles (`constitution.md`, `requirements.md`, `solution.md`, `tasks.md`) with MCP server integration.
- [AI Coding Foundations & Trust](ai-for-software-engineering-skills/ai-coding-foundations.md) - AI coding interaction modes, human accountability, and safe adoption
- [Context, Model & Prompt](ai-for-software-engineering-skills/context-model-prompt.md) - Curate context, route tasks to suitable models, and request verifiable output
- [Specification-Driven Development](ai-for-software-engineering-skills/specification-driven-development.md) - Durable specs, API contracts, task decomposition, and validation
- [Secure Model Selection, Privacy & AI Skills](ai-for-software-engineering-skills/secure-model-selection-and-skills.md) - Private evaluations, data controls, least privilege, and reusable workflows
- [Multi-Agent Coding Workflows](ai-for-software-engineering-skills/multi-agent-coding-workflows.md) - Specialized roles, artifact handoffs, and human phase gates
- [Model Context Protocol (MCP)](ai-for-software-engineering-skills/model-context-protocol.md) - Safe, standard connectivity from AI clients to engineering tools
- [AI PR Review Automation & Hooks](ai-for-software-engineering-skills/ai-pr-review-automation.md) - First-pass review, workflow triggers, and quality automation
- [Agentic Systems Architecture & Frameworks](ai-for-software-engineering-skills/agentic-systems-architecture.md) - Governed agent platforms, BMAD Method, and Superpowers
- [Working with Legacy Codebases](ai-for-software-engineering-skills/legacy-codebase.md) - Map a safe change surface, preserve verified memory, and make small changes with evidence

### 🎓 Learning Resources
- [Courses](courses.md) - AI engineering and solution architecture courses
- [Certifications](certifications.md) - AI engineering, solution architecture and cloud certifications

### 💼 Career Development
- [Career Guide](career.md) - Role snapshots, portfolio tips, and profile building

### 🎯 Interview Preparation
- [Interview Prep](interview-prep.md) - GenAI system design, practice questions, and frameworks

### 🏛️ Solution Architecture
- [Solution Architecture Fundamentals](solution-architecture/solution-architecture-fundamentals.md) - Core architecture principles, patterns, and practices
- [Architectural Patterns & Styles](solution-architecture/architectural-patterns-styles.md) - Design patterns and architectural styles for robust solutions
- [Architecture Decision Records](solution-architecture/architecture-decision-records.md) - Documenting architectural decisions and rationale
- [Clean Architecture](solution-architecture/clean-architecture.md) - Organizing code with dependency inversion and separation of concerns
- [Business Architecture](solution-architecture/business-architecture.md) - Bridge business strategy and technology implementation
- [Technical Architecture](solution-architecture/technical-architecture.md) - Design robust, scalable, and maintainable technical solutions
- [Requirements Analysis](solution-architecture/requirements-analysis.md) - Master requirements analysis and architecturally significant requirements
- [Quality Attributes](solution-architecture/quality-attributes.md) - Master quality attributes and their impact on architecture design
- [Architecture Modeling](solution-architecture/architecture-modeling.md) - Master architecture modeling techniques and notations
- [Architecture Governance](solution-architecture/architecture-governance.md) - Establish effective governance frameworks for architectural consistency
- [Architecture Assessment & Maturity](solution-architecture/architecture-assessment-maturity.md) - Evaluate and improve architectural capabilities
- [Architecture Tools & Practices](solution-architecture/architecture-tools-practices.md) - Master tools, techniques, and practices for effective architecture
- [Cloud Infrastructure](solution-architecture/cloud-infrastructure.md) - Master cloud infrastructure design and deployment
- [Estimation Techniques](solution-architecture/estimation-techniques.md) - Master estimation techniques for accurate project planning
- [Presales Architecture](solution-architecture/presales-architecture.md) - Master presales architecture practices for winning proposals

## 🚀 Introduction

Artificial Intelligence (AI) is reshaping how modern systems are designed. Solution architects are now expected to integrate machine learning models, data pipelines, and intelligent services into scalable and secure architectures that deliver business value.

This repository curates learning resources, certifications, career tips, and interview prep materials to help you grow into an AI‑savvy solution architect or consultant.

## 🎯 What You'll Find Here

- **Plain-language explanations** of complex AI concepts
- **Hands-on checklists** and practical implementation steps
- **Real-world examples** with source attribution and "why it's awesome" explanations
- **Visual diagrams** using Mermaid for architectural clarity
- **Curated resources** from official docs, reputable sources, and "awesome" lists
- **Career guidance** for AI architects, consultants, and solution architects
- **Interview preparation** with system design frameworks and practice questions

## 🚦 Quick Start

1. **New to AI Architecture?** Start with [AI Architecture Patterns](ai-architecture-topics/ai-architecture-patterns.md)
2. **Choosing between models?** Learn [Model Routing](ai-architecture-topics/model-routing.md)
3. **Building RAG systems?** Check [Vector Stores & Embeddings](ai-architecture-topics/vector-stores-and-embeddings.md)
4. **Preparing for interviews?** Jump to [Interview Prep](interview-prep.md)
5. **Career planning?** Explore [Career Guide](career.md)

## 📖 How to Use This Guide

![awesome-ai-architect-welcome.png](img/awesome-ai-architect-welcome.png)

<div align="center">

### ☕📚 Take a sip, learn a bit  
*Grab a drink and enjoy the content and self-development.*

</div>


Each page follows a consistent structure:
- **TL;DR** - Simple explanation in plain language
- **Quickstart** - Actionable steps you can try now
- **The Idea** - Deeper context and concepts
- **Key Concepts** - Core ideas with real-world examples
- **When to Use This** - Clear guidance on applicability
- **Real-World Examples** - Practical implementations with sources
- **Common Pitfalls** - What to avoid and how
- **Next Steps** - Where to learn more

## 📄 License

This project is licensed under the MIT License—see the [LICENSE](LICENSE) file for details.

---

<div align="center">

**Made with ❤️ for the AI Architect community**

*Contributions welcome! Feel free to open issues or submit pull requests.*

</div>
