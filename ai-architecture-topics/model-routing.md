---
title: "Model Routing"
summary: "Dynamically choose the best model for a request using rules, evaluation, or metadata."
---

# Model Routing

> Automatically choose the right AI model for each request to balance cost, speed, and quality.

## TL;DR
- **Model routing** sends each request to the model that's most likely to handle it well.
- **Rule-based routing** uses simple rules like keywords or metadata to pick a model.
- **Confidence-based routing** starts with a cheap model and escalates when confidence is low.
- **Ensemble routing** queries multiple models and combines their answers for better results.

## Quickstart (Do this now)
1. **List your models**: Note their strengths, costs, and latency.
2. **Add a router**: Start with simple if/then rules to select models.
3. **Track confidence**: Measure response quality or uncertainty.
4. **Fallback smartly**: Re-run low-confidence answers on a stronger model.
5. **Experiment with ensembles**: Try majority vote or scoring across models.

## The Idea (Slightly deeper)
Model routing is like having a traffic controller for AI models. Instead of sending every request to the biggest or most expensive model, you route each one to the option that gives the best tradeoff between cost, speed, and accuracy. This can be as simple as keyword rules or as advanced as a learned router model.

## Key Concepts
- **Rule-based routing**: Hard-coded logic chooses models (e.g., "if query mentions 'code', use a coding model").
- **Confidence-based routing**: Start with a fast model and only escalate when the answer is uncertain.
- **Ensemble routing**: Run several models in parallel and combine their outputs (e.g., majority vote or weighted scoring).
- **Router function**: The component that inspects a request and decides which model(s) to invoke.

## When to Use This
- **Use when**: You have multiple models with different strengths or costs.
- **Use when**: You need predictable latency or budget control.
- **Don't use when**: A single model already meets all requirements.
- **Consider alternatives**: Tuning one high‑quality model instead of maintaining many.

## Real-World Examples
- **Rule-based**: OpenAI recommends routing simple tasks to `gpt-3.5` and complex reasoning to `gpt-4` → [OpenAI Model Selection](https://platform.openai.com/docs/guides/text-generation/selecting-model)
- **Confidence-based**: LlamaIndex's Router Query Engine picks a model based on similarity scores and escalates on low confidence → [LlamaIndex Router](https://docs.llamaindex.ai/en/stable/module_guides/advanced/modules/query_engine/route_query_engine/)
- **Ensemble**: Self-consistency techniques run multiple model instances and select the most consistent answer → [Self‑Consistency Paper](https://arxiv.org/abs/2203.11171)

## Common Pitfalls
- **Over-routing**: Too many rules or thresholds can add latency and complexity.
- **No feedback loop**: Without evaluation, routing decisions may degrade over time.
- **Cost surprises**: Escalation to expensive models without limits can blow your budget.

## Next Steps
- **Learn more**: [AI Architecture Patterns](ai-architecture-topics/ai-architecture-patterns.md) - Patterns that often pair with routing strategies
- **Measure it**: [Evaluation & Observability](ai-architecture-topics/evaluation-and-observability.md) - Track routing quality and costs
- **Scale it**: [Serving & Scaling](ai-architecture-topics/serving-and-scaling.md) - Deploy routers and models in production
