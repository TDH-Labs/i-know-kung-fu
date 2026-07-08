# Ollama Model Management Guide

## Installation
```bash
curl -fsSL https://ollama.ai/install.sh | sh
```

## Model Operations
1. **Listing Available Models**:
   ```bash
   ollama list
   ```

2. **Downloading Models**:
   ```bash
   ollama pull gemma:4b  # 4B parameter version
   ollama pull gemma:31b # 31B parameter version (20GB)
   ```

3. **Running Inference**:
   ```bash
   ollama run gemma:4b
   ```
   - First run triggers automatic download if missing
   - Subsequent runs use local cached version

## Model Selection Criteria
- **Gemma 4B**: 9.6GB download, faster inference for smaller tasks
- **Gemma 31B**: 20GB download, higher accuracy for complex tasks

## Performance Characteristics
- Initial query latency: 2-5 seconds (model loading)
- Subsequent queries: sub-second responses
- GPU utilization spikes during generation (monitor via DGX Dashboard)

## Common Issues
1. **Download Interruptions**: Resume partial downloads with same pull command
2. **Memory Errors**:
   - For 31B model: Ensure 20GB+ free memory
   - Close other memory-intensive applications
3. **Version Conflicts**: Explicitly specify model tags (e.g., gemma:4b vs gemma:latest)

## Integration Example with Claude
```bash
ollama launch claude --model gemma:31b
```
- Requires prior Claude installation
- Model specification overrides default