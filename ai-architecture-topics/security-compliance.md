---
title: "Security & Compliance"
summary: "Meet regulatory standards, encrypt data, and track model lineage to build trustworthy AI systems"
---

# Security & Compliance

> Align AI systems with laws, encrypt sensitive data, and track model origins for accountability.

![Security & Compliance](/img/safety-and-security.png)

## TL;DR
- Understand and comply with regulations like GDPR, HIPAA, or SOC 2.
- Encrypt data in transit and at rest using strong key management.
- Track model provenance to record training data, code, and model versions.

## Quickstart (Do this now)
1. **Map regulations**: Determine which laws and frameworks apply to your data and domain.
2. **Enable encryption**: Use TLS for network traffic and managed keys for storage.
3. **Track model lineage**: Log training data sources, code versions, and model hashes.

## The Idea (Slightly deeper)
Regulatory requirements ensure AI systems meet legal and industry standards. Encryption protects data from unauthorized access. Model provenance tracking records how models are built, creating an audit trail for compliance and reproducibility.

## Key Concepts
- **Regulatory Requirements**: GDPR, HIPAA, PCI DSS, and other frameworks dictate how data must be handled.
- **Encryption**: Protects data in transit and at rest; includes key management, HSMs, and secrets rotation.
- **Model Provenance Tracking**: Captures metadata about training datasets, model weights, and deployment history.

## When to Use This
- **Use when**: Handling personal or sensitive data subject to regulation.
- **Use when**: Auditors or customers require proof of data handling practices.
- **Don't use when**: Prototyping with synthetic or public data only.

## Real-World Examples
- **GDPR Compliance**: EU organizations logging model training data to satisfy Article 30 records.
- **Zero Trust Encryption**: Cloud providers offering customer-managed keys for AI workloads.
- **Model Cards**: OpenAI and Google release model cards documenting training data and intended use.

## Common Pitfalls
- **Ignoring regional laws**: Overlooking cross-border data transfer restrictions.
- **Weak key management**: Hard-coded keys or lack of rotation.
- **No audit trail**: Missing metadata makes incident response and compliance reviews difficult.

## Next Steps
- **Learn more**: [Safety & Security](ai-architecture-topics/safety-and-security.md) – Guardrails and threat mitigation.
- **Implement**: [NIST AI RMF](https://www.nist.gov/itl/ai-risk-management-framework) – Risk management guidance for AI systems.
- **Track models**: Use tools like [MLflow](https://mlflow.org/) or [Weights & Biases](https://wandb.ai/) for provenance tracking.
