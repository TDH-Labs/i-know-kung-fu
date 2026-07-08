---
description: Skill for deploying and running local AI models using Ollama on NVIDIA
  DGX Spark hardware, including model download, inference execution, and integration
  with coding tools like Claude.
name: Local AI Model Deployment with Ollama on NVIDIA DGX Spark
tags:
- local-inference
- ollama
- nvidia-dgx
- gemma
- model-deployment
---

# Local AI Model Deployment with Ollama on NVIDIA DGX Spark

> Skill for deploying and running local AI models using Ollama on NVIDIA DGX Spark hardware, including model download, inference execution, and integration with coding tools like Claude.

## Overview
This skill enables you to deploy and run AI models locally on NVIDIA DGX Spark hardware using Ollama. Key capabilities include:
- Local model management (download/version control)
- GPU-accelerated inference
- Integration with development tools like Claude

See hardware requirements in [Hardware Setup](references/hardware_setup.md).

## Step-by-Step Workflow

1. **System Setup**
   - Connect power and peripherals as detailed in [Hardware Setup](references/hardware_setup.md)
   - Boot system and complete Ubuntu initialization

2. **Ollama Installation**
   ```bash
   curl -fsSL https://ollama.ai/install.sh | sh
   ```

3. **Model Download**
   ```bash
   ollama pull gemma:4b  # 9.6GB version
   ollama pull gemma:31b # 20GB version (optional)
   ```

4. **Basic Inference Test**
   ```bash
   ollama run gemma:4b
   ```
   - Verify response quality and speed
   - Monitor GPU utilization in DGX Dashboard

5. **Advanced Integration (with Claude)**
   ```bash
   # Install Claude
   sudo apt install claude-code
   
   # Launch with specific model
   mkdir project
   cd project
   ollama launch claude --model gemma:31b
   ```

## Code Generation Example
```python
# Prompt template for web development
prompt = """Create a static HTML website for yoga accessories with:
1. Responsive navbar
2. Three product cards with images
3. Minimal CSS (inline styles)
4. Contact form placeholder"""

# Send to local model
response = ollama.generate(
    model="gemma:4b",
    prompt=prompt,
    temperature=0.5
)
```

## Best Practices
1. **Model Selection**:
   - Use 4B model for quick prototyping
   - Switch to 31B for production-quality output

2. **Resource Management**:
   - Close unused applications during large model runs
   - Monitor memory usage via DGX Dashboard

3. **Prompt Engineering**:
   - Be specific about output format requirements
   - Include length constraints (e.g., "answer in 3 lines")

## Common Pitfalls
1. **Insufficient Storage**:
   - 31B model requires 20GB+ free space
   - Solution: Clean up unused models with `ollama rm <model>`

2. **GPU Memory Errors**:
   - Symptom: "CUDA out of memory" errors
   - Solution: Use smaller batch sizes or model variants

3. **Stale Model Versions**:
   - Always specify version tag (e.g., `gemma:4b` not just `gemma`)
   - Update models periodically with `ollama pull`

## Validation Steps
1. **Basic Sanity Check**:
   ```bash
   ollama run gemma:4b "Explain quantum computing in simple terms"
   ```
   - Verify coherent response within 5 seconds

2. **GPU Utilization Test**:
   - Run complex query while monitoring DGX Dashboard
   - Expect 50-80% GPU utilization spikes

3. **Code Generation Test**:
   - Generate Python file handling code
   - Verify executable output with `python3 generated_code.py`

For advanced use cases, see [Local Inference Applications](references/local_inference_applications.md).

## 📺 Source Videos

- [NVIDIA DGX Spark - AI Supercomputer: First Impressions](https://www.youtube.com/watch?v=FW8bCjhl3zE) — codebasics

**Difficulty**: Intermediate

## Prerequisites

- basic-linux-commands
- gpu-hardware-understanding
- python-programming
