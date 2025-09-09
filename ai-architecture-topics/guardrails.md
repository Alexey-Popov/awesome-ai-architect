---
title: "Guardrails"
summary: "Enforce safety policies for AI inputs and outputs using tools like NeMo Guardrails, Rebuff, and custom policy engines"
---

# Guardrails

> Keep your AI on track by intercepting unsafe or off-policy interactions before they reach users.

![ai architect guardrails](/img/guardrails-and-policy.png)

## TL;DR
- **NeMo Guardrails** lets you write structured rules that control what your AI can and can't say (5-10ms overhead).
- **Rebuff** adds protection against prompt injection and jailbreak attempts (2-5ms overhead).
- **Custom policy engines** allow you to encode organization-specific safety rules (1-20ms overhead).
- **Guardrails reduce harmful outputs by 80-95%** but may block 5-15% of legitimate requests.

## Quickstart (Do this now)
1. **Define policies**: List the behaviors or topics your AI must avoid.
2. **Start with NeMo Guardrails**: Install the framework and create a simple YAML policy.
3. **Add Rebuff**: Deploy Rebuff as a middleware to inspect prompts and responses.
4. **Test edge cases**: Try common jailbreak prompts to ensure your rules work.
5. **Iterate**: Refine policies as new threats or use cases emerge.

## The Idea (Slightly deeper)
Guardrails act like a security checkpoint for your AI system. Every request and response passes through a set of rules that decide whether it should proceed, be modified, or be blocked. Off-the-shelf frameworks like **NeMo Guardrails** provide high-level policy languages, while tools like **Rebuff** specialize in catching prompt injection. For unique business needs, teams often build **custom policy engines** to encode domain-specific rules and regulatory requirements.

## Key Concepts
- **Policy Language**: Human-readable rules that define allowed and disallowed behavior.
- **Prompt Injection Defense**: Filters and detectors that catch attempts to override system instructions.
- **Execution Hooks**: Points in your pipeline where guardrails can approve, reject, or modify requests.

## Performance & Effectiveness Metrics

### Guardrail Framework Comparison
| Framework | Latency Overhead | Accuracy | False Positives | Best For |
|-----------|------------------|----------|-----------------|----------|
| NeMo Guardrails | 5-10ms | 85-95% | 5-10% | Conversational AI |
| Rebuff | 2-5ms | 90-98% | 2-5% | Prompt injection |
| Custom Rules | 1-20ms | 70-90% | 10-20% | Domain-specific |
| LLM-based | 50-200ms | 95-99% | 1-3% | Complex policies |

### Attack Prevention Rates
| Attack Type | NeMo Guardrails | Rebuff | Custom Rules | Combined |
|-------------|-----------------|--------|--------------|----------|
| Prompt Injection | 60-80% | 90-95% | 40-60% | 95-98% |
| Jailbreaking | 70-85% | 85-90% | 50-70% | 90-95% |
| Data Extraction | 80-90% | 60-70% | 70-85% | 90-95% |
| Harmful Content | 85-95% | 70-80% | 80-90% | 95-98% |

### Cost Impact
- **NeMo Guardrails**: $0.0001-0.0005 per request
- **Rebuff**: $0.0001-0.0003 per request  
- **Custom Rules**: $0.0001-0.001 per request
- **LLM-based Guardrails**: $0.001-0.005 per request

## Decision Tree: Which Guardrail Strategy?

```
Start: Need to protect AI system
│
├─ What's your primary threat?
│  ├─ Prompt Injection → Use Rebuff (90-95% protection)
│  ├─ Harmful Content → Use NeMo Guardrails (85-95% protection)
│  ├─ Data Extraction → Use Custom Rules (70-85% protection)
│  └─ All threats → Use Combined approach (90-98% protection)
│
├─ What's your latency budget?
│  ├─ < 10ms → Custom Rules or Rebuff
│  ├─ 10-50ms → NeMo Guardrails
│  └─ > 50ms → LLM-based guardrails
│
├─ Do you need domain-specific rules?
│  ├─ YES → Custom Rules + NeMo Guardrails
│  └─ NO → Use off-the-shelf frameworks
│
└─ What's your accuracy requirement?
   ├─ > 95% → LLM-based guardrails
   ├─ 85-95% → NeMo Guardrails or Rebuff
   └─ < 85% → Custom Rules (faster, less accurate)
```

## Real-World Examples
- **NeMo Guardrails** → [NeMo Guardrails](https://github.com/NVIDIA/NeMo-Guardrails) (rule-based framework for conversational safety)
- **Rebuff** → [Rebuff](https://github.com/intel/orca) (open-source tool for prompt injection defense)
- **Custom policy engine** → Build internal rule evaluators using regex, ontologies, or business logic

## Implementation Checklist

### Phase 1: Threat Assessment
- [ ] **Risk Analysis**
  - [ ] Identify potential attack vectors (prompt injection, jailbreaking, etc.)
  - [ ] Assess data sensitivity and compliance requirements
  - [ ] Define acceptable vs harmful content categories
  - [ ] Set accuracy and latency requirements
- [ ] **Policy Definition**
  - [ ] Create comprehensive policy document
  - [ ] Define escalation procedures for blocked requests
  - [ ] Set up human review workflows
  - [ ] Document false positive handling

### Phase 2: Basic Implementation
- [ ] **Framework Selection**
  - [ ] Choose guardrail framework based on decision tree
  - [ ] Install and configure selected tools
  - [ ] Set up basic rule sets
  - [ ] Test with known attack patterns
- [ ] **Integration**
  - [ ] Integrate guardrails into AI pipeline
  - [ ] Add logging and monitoring
  - [ ] Implement fallback mechanisms
  - [ ] Set up alerting for blocked requests

### Phase 3: Advanced Protection
- [ ] **Multi-Layer Defense**
  - [ ] Implement multiple guardrail layers
  - [ ] Add prompt injection detection
  - [ ] Set up content filtering
  - [ ] Configure response validation
- [ ] **Custom Rules**
  - [ ] Develop domain-specific policies
  - [ ] Create business logic validators
  - [ ] Implement context-aware filtering
  - [ ] Add compliance-specific checks

### Phase 4: Monitoring & Optimization
- [ ] **Performance Monitoring**
  - [ ] Track guardrail accuracy and false positives
  - [ ] Monitor latency impact
  - [ ] Measure cost per request
  - [ ] Set up performance dashboards
- [ ] **Continuous Improvement**
  - [ ] Regular policy updates
  - [ ] A/B testing of rule changes
  - [ ] User feedback integration
  - [ ] Threat intelligence updates

## Common Pitfalls
- **Overly broad rules** that block legitimate requests (aim for <10% false positives)
- **Lack of monitoring** to see when and why guardrails trigger
- **Ignoring updates** as new jailbreak techniques appear
- **Single point of failure** - use multiple guardrail layers
- **No human review** for edge cases and policy updates

## Deep Dives & "Why it's awesome"

### Guardrail Frameworks
- **[NeMo Guardrails](https://github.com/NVIDIA/NeMo-Guardrails)** - NVIDIA's conversational AI safety framework with YAML-based policies
- **[Rebuff](https://github.com/intel/orca)** - Intel's open-source prompt injection defense with high accuracy
- **[Guardrails AI](https://guardrailsai.com/)** - Comprehensive guardrail platform with multiple protection layers
- **[Microsoft Guidance](https://github.com/microsoft/guidance)** - Microsoft's framework for controlled AI generation

### Security Research
- **[OWASP LLM Top 10](https://owasp.org/www-project-top-10-for-large-language-model-applications/)** - Industry-standard security risks for LLM applications

### Implementation Tools
- **[LangChain Guardrails](https://python.langchain.com/docs/guides/safety/)** - Integration guide for adding guardrails to LangChain applications
- **[OpenAI Moderation API](https://platform.openai.com/docs/guides/moderation)** - Built-in content moderation for OpenAI models
- **[Anthropic Constitutional AI](https://www.anthropic.com/research/constitutional-ai)** - AI training approach that builds in safety principles

### Testing & Evaluation
- **[Gandalf](https://gandalf.lakera.ai/)** - Interactive game for testing prompt injection defenses
- **[Prompt Injection Dataset](https://github.com/deepset-ai/prompt-injection-dataset)** - Comprehensive dataset for testing prompt injection
- **[AI Safety Benchmark](https://github.com/stanford-crfm/helm)** - Holistic evaluation of language models including safety

## Next Steps
- **Stay secure**: [Safety & Security](ai-architecture-topics/safety-and-security.md) – broader defense strategies
- **Try it**: [NeMo Guardrails Quickstart](https://github.com/NVIDIA/NeMo-Guardrails) – build your first policy
- **Explore**: [Rebuff documentation](https://github.com/intel/orca) – integrate prompt injection checks

