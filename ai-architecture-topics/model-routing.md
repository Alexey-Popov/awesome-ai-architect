---
title: "Model Routing"
summary: "Dynamically choose the best model for a request using rules, evaluation, or metadata."
---

# Model Routing

> Send each task to the model that can handle it best while balancing speed, cost, and accuracy.

## TL;DR
- **Rule-based routers** dispatch requests based on simple heuristics like input length.
- **Eval-driven routers** run small probes or embeddings to decide which model to call.
- **Cascade fallbacks** try a cheap model first and escalate if confidence is low.

## Quickstart (Do this now)
1. **List candidate models** and their strengths.
2. **Define routing rules** or evaluation steps.
3. **Implement logging** to track which model was chosen and why.
4. **Monitor performance** and adjust the rules.

## The Idea (Slightly deeper)
Routing logic reduces cost and improves reliability by steering requests to different models. It can be as simple as a switch statement or as advanced as a learned policy that predicts which model will succeed.

## Key Concepts
- **Routing Rules:** Static or dynamic logic that selects a model.
- **Confidence Scores:** Metrics to decide if escalation or fallback is needed.
- **Audit Trails:** Records of routing decisions for debugging and cost analysis.

## When to Use This
- **Mixed workloads** where different models excel at different tasks.
- **Budget-sensitive systems** that prefer cheaper models when possible.
- **High reliability environments** needing fallbacks when a model fails.

## Real-World Examples
- **API gateways** that route simple questions to fast models and complex ones to GPT-4.
- **Document processors** that switch between OCR and NLP models depending on file type.
- **Support bots** that escalate to premium models when user sentiment is negative.

## Common Pitfalls
- **Rule sprawl**: Too many rules can be hard to manage.
- **Unclear metrics**: Without logging and evaluation it's hard to improve routing.
- **Latency penalties**: Complex evaluation steps slow down responses.

## Next Steps
- **Combine with ensembles**: [Multi-LLM Strategies](multi-llm.md) shows how to blend outputs after routing.

