---
title: "On-Device vs VM"
summary: "Compare running AI models on-device versus in virtual machines, focusing on latency, privacy, and hardware trade-offs"
---

# On-Device vs VM

> Choose the right deployment strategy by understanding how latency, privacy, and hardware shape on-device and virtual machine inference.

![on-device vs vm](/img/on-device-vs-vm.png)

## TL;DR
- **Latency**: On-device inference avoids network hops for instant responses (5-50ms), while VM-hosted models add round-trip delays (100-500ms).
- **Privacy**: Keeping data local improves confidentiality; sending it to a VM increases exposure and compliance risks.
- **Hardware**: Devices have limited memory and compute (2-8GB RAM), whereas VMs can scale with specialized accelerators (up to 80GB VRAM).
- **Cost**: On-device has zero per-request costs, VM costs scale with usage ($0.001-0.06 per 1K tokens).

## Quickstart (Do this now)
1. **Scope your model**: Check if the model fits within memory and compute constraints of target devices.
2. **Measure latency needs**: If every millisecond matters, favor on-device; if not, remote VMs may suffice.
3. **Review data policies**: Confirm whether data can leave the device before choosing a VM deployment.

## The Idea
Running AI models locally delivers low-latency, private experiences but requires efficient models tailored to device hardware. Virtual machines offer abundant resources and simpler updates at the cost of network latency and potential privacy trade-offs.

## Key Concepts
- **Latency budgets** – Edge inference removes network delays but may be slower if the device hardware is weak.
- **Privacy boundaries** – Processing sensitive data locally reduces the risk of interception or misuse.
- **Hardware selection** – VMs can leverage GPUs or TPUs; devices may rely on mobile CPUs or NPUs.

## Performance & Cost Comparison

### Latency Comparison (LLaMA-7B)
| Deployment | Hardware | Latency | Network | Total Latency |
|------------|----------|---------|---------|---------------|
| On-Device | iPhone 15 Pro | 200-500ms | 0ms | 200-500ms |
| On-Device | MacBook M3 | 100-300ms | 0ms | 100-300ms |
| On-Device | RTX 4090 | 50-150ms | 0ms | 50-150ms |
| VM | A100 (same region) | 100-200ms | 10-50ms | 110-250ms |
| VM | A100 (cross-region) | 100-200ms | 100-300ms | 200-500ms |

### Memory Requirements
| Model Size | On-Device RAM | VM VRAM | On-Device Feasible |
|------------|---------------|---------|-------------------|
| 3B parameters | 6-8GB | 8GB | High-end phones, laptops |
| 7B parameters | 14-16GB | 16GB | High-end laptops only |
| 13B parameters | 26-32GB | 32GB | Desktop/workstation |
| 70B parameters | 140GB+ | 80GB+ | VM only |

### Cost Analysis (per 1K tokens)
| Deployment | Hardware Cost | Inference Cost | Total Cost |
|------------|---------------|----------------|------------|
| On-Device | $0 (owned) | $0 | $0 |
| VM (A100) | $3/hour | $0.001-0.005 | $0.001-0.005 |
| VM (H100) | $8/hour | $0.001-0.003 | $0.001-0.003 |
| API (OpenAI) | $0 | $0.002-0.06 | $0.002-0.06 |

### Privacy & Compliance
| Aspect | On-Device | VM | API |
|--------|-----------|----|----|
| Data leaves device | No | Yes | Yes |
| GDPR compliance | Easy | Complex | Complex |
| HIPAA compliance | Easy | Requires BAA | Requires BAA |
| Audit trail | Device logs | Cloud logs | Provider logs |

## Decision Tree: On-Device vs VM?

```
Start: Need to deploy AI model
│
├─ Is data privacy critical?
│  ├─ YES → On-device (data never leaves device)
│  └─ NO → Continue to next question
│
├─ What's your model size?
│  ├─ < 3B parameters → On-device (fits on most devices)
│  ├─ 3B-7B parameters → Depends on device specs
│  └─ > 7B parameters → VM (too large for most devices)
│
├─ What's your latency requirement?
│  ├─ < 100ms → On-device (no network latency)
│  ├─ 100-500ms → Either (depends on device power)
│  └─ > 500ms → VM (can use powerful hardware)
│
├─ Do you need offline capability?
│  ├─ YES → On-device (no internet required)
│  └─ NO → Continue to next question
│
└─ What's your budget?
   ├─ Low/zero per-request → On-device (one-time hardware cost)
   └─ Flexible → VM (pay-per-use)
```

## When to Use This
- **On-device**: Offline apps, real-time interaction, strict data sovereignty, cost-sensitive applications
- **VM**: Large models, centralized management, bursty workloads, frequent updates needed
- **Hybrid**: Use on-device for simple tasks, VM for complex reasoning

## Real-World Examples
- Smartphones translating speech without an internet connection.
- Cloud-hosted LLMs serving multiple tenants via API.

## Implementation Checklist

### Phase 1: Assessment
- [ ] **Requirements Analysis**
  - [ ] Define latency requirements (< 100ms = on-device preferred)
  - [ ] Assess privacy/compliance needs (GDPR, HIPAA, etc.)
  - [ ] Determine model size and memory requirements
  - [ ] Evaluate offline capability needs
- [ ] **Hardware Evaluation**
  - [ ] Test model on target devices (phones, laptops, etc.)
  - [ ] Measure inference latency and accuracy
  - [ ] Check thermal throttling and battery impact
  - [ ] Compare with VM performance benchmarks

### Phase 2: On-Device Implementation
- [ ] **Model Optimization**
  - [ ] Apply quantization (INT8, FP16) for size reduction
  - [ ] Use model pruning to reduce parameters
  - [ ] Implement dynamic batching for efficiency
  - [ ] Test accuracy vs performance trade-offs
- [ ] **Deployment Setup**
  - [ ] Choose inference framework (ONNX, TensorFlow Lite, Core ML)
  - [ ] Implement model loading and caching
  - [ ] Add error handling and fallback mechanisms
  - [ ] Set up performance monitoring

### Phase 3: VM Implementation
- [ ] **Infrastructure Setup**
  - [ ] Choose cloud provider and instance type
  - [ ] Configure auto-scaling policies
  - [ ] Set up load balancing and health checks
  - [ ] Implement cost monitoring and alerts
- [ ] **Model Deployment**
  - [ ] Deploy model with appropriate serving framework
  - [ ] Configure batch processing for efficiency
  - [ ] Set up model versioning and rollback
  - [ ] Implement caching strategies

### Phase 4: Hybrid Strategy
- [ ] **Intelligent Routing**
  - [ ] Implement request classification (simple vs complex)
  - [ ] Route simple tasks to on-device, complex to VM
  - [ ] Add fallback mechanisms between strategies
  - [ ] Monitor performance and cost across both
- [ ] **Optimization**
  - [ ] A/B test different routing strategies
  - [ ] Optimize based on usage patterns
  - [ ] Implement cost-aware routing
  - [ ] Set up comprehensive monitoring

## Common Pitfalls
- **Ignoring thermal limits**: Edge devices throttle performance when overheating
- **Underestimating network latency**: Cross-region VM calls can add 200-500ms
- **Memory constraints**: Large models may not fit on target devices
- **Battery drain**: On-device inference can significantly impact battery life
- **Model updates**: On-device models are harder to update than VM deployments

## Deep Dives & "Why it's awesome"

### On-Device Frameworks
- **[TensorFlow Lite](https://www.tensorflow.org/lite)** - Google's framework for mobile and edge AI with quantization support
- **[ONNX Runtime](https://onnxruntime.ai/)** - Cross-platform inference engine supporting multiple hardware backends
- **[Core ML](https://developer.apple.com/machine-learning/core-ml/)** - Apple's framework for iOS/macOS with hardware acceleration
- **[MediaPipe](https://mediapipe.dev/)** - Google's framework for real-time on-device ML pipelines

### Edge AI Tools
- **[OpenVINO](https://docs.openvino.ai/)** - Intel's toolkit for optimizing AI inference on edge devices
- **[TensorRT](https://developer.nvidia.com/tensorrt)** - NVIDIA's inference optimization for edge GPUs
- **[Qualcomm AI Engine](https://developer.qualcomm.com/software/ai-stack)** - Snapdragon-optimized AI inference
- **[Arm NN](https://developer.arm.com/ip-products/processors/machine-learning/arm-nn)** - Arm's neural network inference engine

### VM & Cloud Platforms
- **[AWS SageMaker](https://aws.amazon.com/sagemaker/)** - Managed ML platform with inference endpoints
- **[Google Cloud AI Platform](https://cloud.google.com/ai-platform)** - End-to-end ML platform with custom prediction
- **[Azure Machine Learning](https://azure.microsoft.com/en-us/products/machine-learning)** - Enterprise ML platform with real-time inference
- **[Replicate](https://replicate.com/)** - Simple API for running ML models in the cloud

### Performance Benchmarking
- **[MLPerf Mobile](https://mlcommons.org/en/inference-mobile/)** - Industry benchmarks for mobile AI inference
- **[AI Benchmark](https://ai-benchmark.com/)** - Comprehensive mobile AI performance testing
- **[Edge AI Performance](https://github.com/microsoft/EdgeML)** - Microsoft's edge AI optimization tools

## Next Steps
- **Explore**: [AI Architecture Patterns](ai-architecture-topics/ai-architecture-patterns.md) for hybrid approaches
- **Prototype**: [TensorFlow Lite](https://www.tensorflow.org/lite) or [ONNX Runtime](https://onnxruntime.ai/) for edge deployments
- **Scale**: [Serving & Scaling](ai-architecture-topics/serving-and-scaling.md) for production VM deployments