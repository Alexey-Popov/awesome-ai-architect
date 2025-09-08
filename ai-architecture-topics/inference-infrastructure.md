---
title: "Inference Infrastructure"
summary: "Select the right hardware and optimizations for fast, cost-effective model serving"
---

# Inference Infrastructure

> Choose GPUs, TPUs, and model optimizations that deliver the best performance for your budget.

## TL;DR
- **GPUs vs TPUs**: GPUs offer broad framework support while TPUs deliver high throughput for supported models.
- **Quantization** shrinks model size, fitting more instances on a device with minor accuracy trade-offs.
- **Cost-performance metrics** like tokens-per-second-per-dollar keep infrastructure efficient.

## Quickstart (Do this now)
1. **Profile hardware**: Benchmark GPUs, TPUs, or CPUs for your model.
2. **Apply quantization**: Use INT8 or FP8 formats to cut memory use.
3. **Measure throughput**: Track tokens/sec and latency across configs.
4. **Calculate cost**: Divide hourly instance price by tokens served to gauge efficiency.
5. **Monitor utilization**: Watch GPU/TPU usage to right-size instances.

## The Idea (Slightly deeper)
Picking the right accelerator balances raw speed, memory capacity, and framework compatibility. Quantization techniques reduce precision to lower memory and compute needs. Tracking cost against performance ensures the chosen setup scales sustainably.

## Key Concepts
- **Accelerator Selection**: Comparing NVIDIA GPUs, Google TPUs, and CPU alternatives.
- **Memory Bandwidth**: Impacts how quickly models read data during inference.
- **Model Quantization**: INT8, FP8, and sparsity to shrink model footprints.
- **Throughput Metrics**: Tokens/sec, latency, and cost per million tokens.
- **Utilization**: Keeping devices busy to avoid paying for idle capacity.

## When to Use This
- **Use when**: Deploying models with strict latency or cost requirements.
- **Use when**: Deciding between on-prem and cloud accelerators.
- **Don't use when**: Prototyping small models on a laptop.
- **Consider alternatives**: Managed inference services for minimal ops overhead.

## Real-World Examples
- **NVIDIA A100**: Versatile GPU with strong mixed-precision support → [A100](https://www.nvidia.com/en-us/data-center/a100/)
- **Google TPU v5e**: High throughput for transformer workloads → [TPU v5e](https://cloud.google.com/tpu/docs/system-architecture-tpu-vm#v5e)
- **GPTQ**: Popular open-source quantization method → [GPTQ](https://github.com/IST-DASLab/gptq)
- **AWS Inferentia2**: Custom silicon optimized for large language models → [Inferentia2](https://aws.amazon.com/machine-learning/inferentia/)

## Common Pitfalls
- **Overprovisioning**: Paying for accelerators that sit idle.
- **Unsupported quantization**: Some models lose too much accuracy or fail to run.
- **Ignoring bandwidth**: Fast cores are wasted if memory can't keep up.
- **No cost tracking**: Missing tokens-per-dollar metrics hides inefficiency.

## Next Steps
- **Learn more**: [Serving & Scaling](ai-architecture-topics/serving-and-scaling.md) - Deploy optimized models in production
- **Measure**: [Evaluation & Observability](ai-architecture-topics/evaluation-and-observability.md) - Monitor latency and spending
- **Explore**: [Orchestration Frameworks](ai-architecture-topics/orchestration-frameworks.md) - Manage multi-model pipelines

