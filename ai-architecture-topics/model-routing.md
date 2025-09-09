---
title: "Model Routing"
summary: "Dynamically choose the best model for a request using rules, evaluation, or metadata."
---

# Model Routing

> Automatically choose the right AI model for each request to balance cost, speed, and quality.

![Model Routing](/img/model-routing.png)

## TL;DR
- **Model routing** sends each request to the model that's most likely to handle it well.
- **Rule-based routing** uses simple rules like keywords or metadata to pick a model (0-5ms overhead).
- **Confidence-based routing** starts with a cheap model and escalates when confidence is low (2-3x cost savings).
- **Ensemble routing** queries multiple models and combines their answers for better results (3-5x cost increase).

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

## Cost & Performance Metrics

### Routing Strategy Impact
| Strategy | Overhead | Cost Impact | Accuracy Impact | Use Case |
|----------|----------|-------------|-----------------|----------|
| Rule-based | 0-5ms | Neutral | +5-10% | Simple categorization |
| Confidence-based | 10-50ms | -40-60% | +10-15% | Cost optimization |
| Ensemble | 50-200ms | +200-400% | +15-25% | Maximum accuracy |
| Learned routing | 20-100ms | -20-40% | +20-30% | Complex patterns |

### Cost Optimization Examples
- **Confidence-based routing**: 60% cost reduction with 12% accuracy improvement
- **Rule-based routing**: 40% cost reduction for categorized requests
- **Ensemble routing**: 25% accuracy improvement for 3x cost increase

## Decision Tree: Which Routing Strategy to Use?

```
Start: Need to route requests to different models
│
├─ Is cost the primary concern?
│  ├─ YES → Do you have clear request categories?
│  │  ├─ YES → Use Rule-based routing (40% cost savings)
│  │  └─ NO → Use Confidence-based routing (60% cost savings)
│  └─ NO → Is accuracy the primary concern?
│     ├─ YES → Use Ensemble routing (25% accuracy gain, 3x cost)
│     └─ NO → Use Learned routing (20% accuracy gain, 20% cost savings)
│
├─ Do you have historical routing data?
│  ├─ YES → Train a learned router model
│  └─ NO → Start with rule-based, collect data, then upgrade
│
└─ What's your latency budget?
   ├─ < 200ms → Rule-based or confidence-based
   ├─ 200-500ms → Confidence-based or learned routing
   └─ > 500ms → Ensemble routing acceptable
```

## When to Use This
- **Rule-based**: Clear request categories, cost optimization, low latency needs
- **Confidence-based**: Cost optimization with quality maintenance, uncertain request types
- **Ensemble**: Maximum accuracy needed, high-value decisions, flexible budget
- **Learned routing**: Complex patterns, historical data available, balanced requirements

## Real-World Examples
- **Rule-based**: OpenAI recommends routing simple tasks to `gpt-chat` models and complex reasoning to `gpt-reasoning`
- **Confidence-based**: LlamaIndex's Router Query Engine picks a model based on similarity scores and escalates on low confidence 
- **Ensemble**: Self-consistency techniques run multiple model instances and select the most consistent answer 

## Implementation Checklist

### Phase 1: Setup
- [ ] **Model Inventory**
  - [ ] List all available models with costs, latency, and capabilities
  - [ ] Define model strengths and weaknesses
  - [ ] Set up monitoring for each model
- [ ] **Basic Routing**
  - [ ] Implement simple rule-based router
  - [ ] Add request categorization logic
  - [ ] Set up A/B testing framework
  - [ ] Monitor routing decisions and outcomes

### Phase 2: Optimization
- [ ] **Confidence-based Routing**
  - [ ] Implement confidence scoring for responses
  - [ ] Set confidence thresholds for escalation
  - [ ] Add fallback mechanisms
  - [ ] Measure cost savings and accuracy impact
- [ ] **Performance Tuning**
  - [ ] Optimize router latency
  - [ ] Implement caching for routing decisions
  - [ ] Add circuit breakers for model failures
  - [ ] Set up cost alerts and budgets

### Phase 3: Advanced Features
- [ ] **Ensemble Routing** (if needed)
  - [ ] Implement parallel model execution
  - [ ] Add response combination logic
  - [ ] Set up consensus mechanisms
  - [ ] Monitor ensemble performance vs single models
- [ ] **Learned Routing** (if data available)
  - [ ] Collect historical routing data
  - [ ] Train routing model
  - [ ] Implement online learning
  - [ ] A/B test against rule-based routing

### Phase 4: Production
- [ ] **Monitoring & Observability**
  - [ ] Track routing accuracy and costs
  - [ ] Set up alerts for routing failures
  - [ ] Implement routing analytics dashboard
  - [ ] Add performance regression detection
- [ ] **Governance**
  - [ ] Document routing rules and logic
  - [ ] Set up routing change approval process
  - [ ] Implement routing rollback mechanisms
  - [ ] Add compliance and audit logging

## Common Pitfalls
- **Over-routing**: Too many rules or thresholds can add latency and complexity.
- **No feedback loop**: Without evaluation, routing decisions may degrade over time.
- **Cost surprises**: Escalation to expensive models without limits can blow your budget.
- **Ignoring model drift**: Models may change performance over time, requiring router updates.

## Deep Dives & "Why it's awesome"

### Tools & Frameworks
- **[Semantic Router](https://github.com/aurelio-labs/semantic-router)** - Open-source semantic routing for LLMs with vector-based classification
- **[OpenRouter](https://openrouter.ai/)** - Unified API for multiple LLM providers with automatic routing


## Next Steps
- **Learn more**: [AI Architecture Patterns](ai-architecture-topics/ai-architecture-patterns.md) - Patterns that often pair with routing strategies
- **Measure it**: [Evaluation & Observability](ai-architecture-topics/evaluation-and-observability.md) - Track routing quality and costs
- **Scale it**: [Serving & Scaling](ai-architecture-topics/serving-and-scaling.md) - Deploy routers and models in production
