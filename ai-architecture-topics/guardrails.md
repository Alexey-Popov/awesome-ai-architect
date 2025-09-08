---
title: "Guardrails"
summary: "Enforce safety policies for AI inputs and outputs using tools like NeMo Guardrails, Rebuff, and custom policy engines"
---

# Guardrails

> Keep your AI on track by intercepting unsafe or off-policy interactions before they reach users.

![ai architect guardrails](/img/safety-and-security.png)

## TL;DR
- **NeMo Guardrails** lets you write structured rules that control what your AI can and can't say.
- **Rebuff** adds protection against prompt injection and jailbreak attempts.
- **Custom policy engines** allow you to encode organization-specific safety rules.

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

## Real-World Examples
- **NeMo Guardrails** → [NeMo Guardrails](https://github.com/NVIDIA/NeMo-Guardrails) (rule-based framework for conversational safety)
- **Rebuff** → [Rebuff](https://github.com/intel/orca) (open-source tool for prompt injection defense)
- **Custom policy engine** → Build internal rule evaluators using regex, ontologies, or business logic

## Common Pitfalls
- **Overly broad rules** that block legitimate requests
- **Lack of monitoring** to see when and why guardrails trigger
- **Ignoring updates** as new jailbreak techniques appear

## Next Steps
- **Stay secure**: [Safety & Security](ai-architecture-topics/safety-and-security.md) – broader defense strategies
- **Try it**: [NeMo Guardrails Quickstart](https://docs.anyscale.com/guardrails/getting-started) – build your first policy
- **Explore**: [Rebuff documentation](https://github.com/intel/orca) – integrate prompt injection checks

