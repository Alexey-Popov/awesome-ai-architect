---
title: "Inference Infrastructure"
summary: "Select the right hardware and optimizations for fast, cost-effective model serving"
---

# Inference Infrastructure

> Choose GPUs, TPUs, and model optimizations that deliver the best performance for your budget.

![Inference Infrastructure](/img/inference-and-optimization.png)

## TL;DR
- **GPUs vs TPUs**: GPUs offer broad framework support while TPUs deliver 2-3x higher throughput for supported models.
- **Quantization** shrinks model size by 50-75%, fitting more instances on a device with <2% accuracy loss.
- **Cost-performance metrics** like tokens-per-second-per-dollar keep infrastructure efficient (target: >1000 tokens/$).

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

## Hardware Performance & Cost Metrics

### GPU Performance Comparison (LLaMA-7B)
| GPU | Memory | Tokens/sec | Latency | Cost/hour | Tokens/$/hour | Best For |
|-----|--------|------------|---------|-----------|---------------|----------|
| RTX 4090 | 24GB | 150-200 | 50-100ms | $0.50 | 300-400 | Development, small models |
| A100 40GB | 40GB | 300-400 | 30-80ms | $3.00 | 100-130 | Production, medium models |
| A100 80GB | 80GB | 400-600 | 25-60ms | $4.50 | 90-130 | Large models, high throughput |
| H100 | 80GB | 800-1200 | 15-40ms | $8.00 | 100-150 | Maximum performance |

### TPU Performance (GPT-3.5 scale)
| TPU Type | Tokens/sec | Latency | Cost/hour | Tokens/$/hour | Best For |
|----------|------------|---------|-----------|---------------|----------|
| TPU v4 | 200-300 | 100-200ms | $2.50 | 80-120 | Transformer workloads |
| TPU v5e | 400-600 | 50-150ms | $4.00 | 100-150 | High throughput |
| TPU v5p | 800-1200 | 30-100ms | $8.00 | 100-150 | Maximum performance |

### Quantization Impact
| Method | Size Reduction | Speed Up | Accuracy Loss | Use Case |
|--------|----------------|----------|---------------|----------|
| INT8 | 50% | 1.5-2x | 1-2% | Production inference |
| FP8 | 50% | 1.3-1.8x | 0.5-1% | High precision needed |
| INT4 | 75% | 2-3x | 2-5% | Edge deployment |
| Sparsity | 60-80% | 1.2-1.5x | 1-3% | Memory-constrained |

### Cost Optimization Targets
- **Tokens per dollar**: >1000 tokens/$ for cost-effective inference
- **GPU utilization**: >80% to justify cloud costs
- **Latency budget**: <200ms for real-time applications
- **Memory efficiency**: <80% of available GPU memory

## Decision Tree: Which Hardware to Choose?

```
Start: Need to deploy AI model for inference
│
├─ What's your model size?
│  ├─ < 7B parameters → RTX 4090 or CPU (cost-effective)
│  ├─ 7B-13B parameters → A100 40GB or TPU v4
│  ├─ 13B-70B parameters → A100 80GB or TPU v5e
│  └─ > 70B parameters → H100 or TPU v5p (or model sharding)
│
├─ What's your latency requirement?
│  ├─ < 50ms → H100 or TPU v5p (premium hardware)
│  ├─ 50-200ms → A100 or TPU v4 (balanced)
│  └─ > 200ms → RTX 4090 or CPU (cost-optimized)
│
├─ What's your budget?
│  ├─ < $1/hour → RTX 4090 or CPU
│  ├─ $1-5/hour → A100 40GB or TPU v4
│  └─ > $5/hour → A100 80GB, H100, or TPU v5e/v5p
│
└─ Do you need quantization?
   ├─ YES → INT8 for production, FP8 for precision
   └─ NO → Use full precision (FP16/FP32)
```

## When to Use This
- **RTX 4090**: Development, small models, cost-sensitive applications
- **A100 40GB**: Production medium models, balanced cost/performance
- **A100 80GB**: Large models, high throughput, memory-intensive workloads
- **H100**: Maximum performance, low latency, high-value applications
- **TPUs**: Google Cloud ecosystem, transformer-optimized workloads
- **CPU**: Very small models, batch processing, cost optimization

## Real-World Examples
- **NVIDIA A100**: Versatile GPU with strong mixed-precision support → [A100](https://www.nvidia.com/en-us/data-center/a100/)
- **Google TPU v5e**: High throughput for transformer workloads → [TPU v5e](https://cloud.google.com/tpu/docs/system-architecture-tpu-vm#v5e)
- **GPTQ**: Popular open-source quantization method → [GPTQ](https://github.com/IST-DASLab/gptq)
- **AWS Inferentia2**: Custom silicon optimized for large language models → [Inferentia2](https://aws.amazon.com/machine-learning/inferentia/)

## Implementation Checklist

### Phase 1: Hardware Selection
- [ ] **Model Profiling**
  - [ ] Measure model size and memory requirements
  - [ ] Test inference latency on different hardware
  - [ ] Calculate tokens-per-second benchmarks
  - [ ] Estimate cost per inference
- [ ] **Hardware Procurement**
  - [ ] Choose hardware based on decision tree
  - [ ] Set up cloud instances or on-prem hardware
  - [ ] Configure CUDA/TPU drivers and frameworks
  - [ ] Test basic inference functionality

### Phase 2: Optimization
- [ ] **Quantization**
  - [ ] Test INT8 quantization with accuracy evaluation
  - [ ] Implement FP8 if supported by hardware
  - [ ] Measure speedup and accuracy trade-offs
  - [ ] Deploy quantized model to production
- [ ] **Performance Tuning**
  - [ ] Optimize batch sizes for throughput
  - [ ] Implement dynamic batching
  - [ ] Configure memory management
  - [ ] Set up GPU utilization monitoring

### Phase 3: Production Setup
- [ ] **Monitoring & Observability**
  - [ ] Track tokens-per-second metrics
  - [ ] Monitor GPU/TPU utilization
  - [ ] Set up cost per inference tracking
  - [ ] Implement performance alerts
- [ ] **Scaling & Reliability**
  - [ ] Configure auto-scaling policies
  - [ ] Implement load balancing
  - [ ] Set up health checks
  - [ ] Plan for hardware failures

### Phase 4: Cost Optimization
- [ ] **Cost Analysis**
  - [ ] Calculate total cost of ownership
  - [ ] Compare cloud vs on-prem costs
  - [ ] Identify cost optimization opportunities
  - [ ] Set up budget alerts
- [ ] **Continuous Optimization**
  - [ ] Regular performance reviews
  - [ ] Hardware upgrade planning
  - [ ] Model optimization updates
  - [ ] Cost trend analysis

## Common Pitfalls
- **Overprovisioning**: Paying for accelerators that sit idle.
- **Unsupported quantization**: Some models lose too much accuracy or fail to run.
- **Ignoring bandwidth**: Fast cores are wasted if memory can't keep up.
- **No cost tracking**: Missing tokens-per-dollar metrics hides inefficiency.
- **Ignoring utilization**: Low GPU utilization means wasted money.

## Deep Dives & "Why it's awesome"

### Hardware Guides
- **[NVIDIA A100 Performance Guide](https://www.nvidia.com/en-us/data-center/a100/)** - Comprehensive performance data and optimization tips for A100 GPUs
- **[Google TPU Performance](https://cloud.google.com/tpu/docs/performance-models)** - TPU performance characteristics and optimization strategies
- **[AWS Inferentia2 Documentation](https://aws.amazon.com/machine-learning/inferentia/)** - Custom silicon for cost-effective inference at scale

### Quantization Tools
- **[GPTQ Implementation](https://github.com/IST-DASLab/gptq)** - Post-training quantization for large language models
- **[AWQ: Activation-aware Weight Quantization](https://github.com/mit-han-lab/awq)** - Advanced quantization with minimal accuracy loss
- **[TensorRT-LLM](https://github.com/NVIDIA/TensorRT-LLM)** - High-performance inference optimization for NVIDIA GPUs

### Performance Benchmarking
- **[MLPerf Inference Benchmarks](https://mlcommons.org/en/inference/)** - Industry-standard AI inference benchmarks
- **[Hugging Face Inference Benchmarks](https://huggingface.co/spaces/optimum/benchmark)** - Real-world performance testing for transformer models
- **[vLLM Performance Guide](https://docs.vllm.ai/en/latest/performance/)** - High-throughput inference optimization techniques

### Cost Optimization
- **[Cloud GPU Pricing Comparison](https://www.cloud-gpu.com/)** - Real-time pricing across cloud providers
- **[AWS EC2 GPU Pricing](https://aws.amazon.com/ec2/pricing/on-demand/)** - Detailed pricing for AWS GPU instances
- **[Google Cloud TPU Pricing](https://cloud.google.com/tpu/pricing)** - TPU pricing and cost optimization strategies

## Next Steps
- **Learn more**: [Serving & Scaling](serving-and-scaling.md) - Deploy optimized models in production
- **Measure**: [Evaluation & Observability](evaluation-and-observability.md) - Monitor latency and spending
- **Explore**: [Orchestration Frameworks](orchestration-frameworks.md) - Manage multi-model pipelines

