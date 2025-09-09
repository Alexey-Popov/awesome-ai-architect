---
title: "Observability"
summary: "Monitor AI systems with Prometheus, OpenTelemetry, drift detection, and alerting best practices"
---

# Observability

> Keep your AI systems healthy with actionable metrics, traces, and alerts.

![observability](/img/logging-and-monitoring.png)

## TL;DR
- **Prometheus** collects and stores metrics so you can see how your system behaves.
- **OpenTelemetry** standardizes traces and metrics across services.
- **Drift detection** spots when model behavior shifts away from training baselines.
- **Alerting** notifies your team before users notice problems.

## Quickstart (Do this now)
1. **Deploy Prometheus**: scrape metrics from your services.
2. **Instrument with OpenTelemetry**: emit traces and metrics in a vendor-neutral format.
3. **Enable drift detection**: compare live predictions against reference data.
4. **Configure alerts**: set thresholds for latency, errors, and drift.
5. **Build dashboards**: visualize key metrics and trace data.

## The Idea (Slightly deeper)
Observability lets you understand the internal state of your AI system from the outside. Prometheus gathers time-series metrics and offers powerful queries. OpenTelemetry provides a unified standard for emitting metrics, logs, and traces. Drift detection monitors data and model output to catch changes that degrade performance. Alerting ties it all together by triggering notifications when metrics cross predefined thresholds.

## Diagram
![Observability Diagram](/img/diagrams/evaluation-and-observability.png)

## Key Concepts
- **Metrics collection** with Prometheus
- **Distributed tracing** with OpenTelemetry
- **Model drift detection** for data and performance shifts
- **Alerting rules** to notify on anomalies

## When to Use This
- **Use when**: running AI systems in production where reliability matters
- **Use when**: monitoring model quality over time
- **Don't use when**: exploring prototypes without uptime requirements
- **Consider alternatives**: simple logging for throwaway experiments

## Real-World Examples
- **Prometheus** → [Prometheus](https://prometheus.io/) (open-source metrics platform with alerting)
- **OpenTelemetry** → [OpenTelemetry](https://opentelemetry.io/) (standard for traces and metrics)
- **Arize AI** → [Arize](https://arize.com/) (drift detection and monitoring platform)

## Common Pitfalls
- **No alerting**: metrics without alerts won't wake anyone up
- **Ignoring drift**: models can silently degrade without monitoring
- **Fragmented tooling**: inconsistent observability stacks make debugging harder

## Deep Dives & "Why it's awesome"
- **[Prometheus Documentation](https://prometheus.io/docs/introduction/overview/)** - Learn how to collect and query metrics
- **[OpenTelemetry Docs](https://opentelemetry.io/docs/)** - Instrument services once and export anywhere
- **[Evidently AI Drift Detection](https://docs.evidentlyai.com/)** - Open-source library for monitoring data and model drift

## Next Steps
- **Learn more**: [Evaluation & Observability](evaluation-and-observability.md) - Broader strategies for testing and monitoring AI systems
- **Try it**: [Prometheus Quickstart](https://prometheus.io/docs/prometheus/latest/getting_started/)
- **Connect**: [OpenTelemetry Community](https://github.com/open-telemetry/community)

