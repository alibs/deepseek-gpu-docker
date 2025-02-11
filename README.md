---

# DeepSeek AI with Ollama in Docker Container - Usage Guide

## Overview
This guide provides instructions for running the DeepSeek AI platform with Ollama, a popular Python-based AI engine optimized for GPU usage. The setup allows you to run multiple models simultaneously while leveraging the power of NVIDIA GPUs.

---

## prerequisites
- NVIDIA Pascal, Ampere, or Volta GPU (for latest versions of PyTorch)
- CUDA 12.0+ installed with PyTorch 19+
- Python 3.8+
- Ollama installed as a subprocess

---

## Docker Setup Details

### Building the Environment
```bash
docker build -t deepseek-ai .
 ```

### Running Docker
```bash
sudo docker-compose up -d
```

### Setting Up CUDA Runtime
Make sure CUDA Runtime is configured in `~/.kde/cuda/` to enable PyTorch.

---

## Running Instructions

### Creating a DeepSeek AI Container
```bash
docker run -p 50000:5000 -p 12080:6000 deepseek-ai@ollama-project-name
```

### Running an Ollama Process
```bash
ollama start --container_name=deepseek-ai
```

Or as a subprocess:
```bash
ollama start
```

To access documentation, run:
```bash
ollama go to -n <container_name>
```

---

## Model Examples

### Example 1: `deepseek-r1`
```python
ollama run 'deepseek-r1 --model=r1-0750c'
```

**Output**:
```json
{
  "model": {
    "input_size": 224,
    "output_size": 1e6,
    "params": 3.8e9
  },
  "meta": {
    "precision": 'f32',
    "use_cache": True,
    "temperature": 0.5,
    "top_p": 0.9,
    "max_length": 2048
  }
}
```

---

### Example 2: `deepseek-r5`
```python
ollama run 'deepseek-r5 --model=r5-32m'
```

**Output**:
```json
{
  "model": {
    "input_size": 224,
    "output_size": 1e6,
    "params": 1.7e10
  },
  "meta": {
    "precision": 'f32',
    "use_cache": True,
    "temperature": 0.5,
    "top_p": 0.9,
    "max_length": 2048
  }
}
```

---

## Notes

- **Depends on CUDA Runtime**: Ollama requires CUDA Runtime to run the GPU-accelerated models.
- **Best Practices**:
  - Use official model parameters for compatibility with Ollama.
  - Ensure you have a stable internet connection when running containers and starting processes.
- **Documentation**: For detailed instructions, visit the [DeepSeek AI documentation](https://deepseek.ai/docs).

---

## Pulling Models

```bash
ollama pull 'deepseek-r1'
```

List of supported models:
- `deepseek-r1`
- `deepseek-r5`
- `deepseek-cos`  
- `deepseek-sin`  
- `deepseek-math`

To view all available models:
```bash
ollama list --model
```

---

--- 
