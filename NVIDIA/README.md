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
```CMD
docker build -t deepseek-gpu-docker .
 ```

### Running Docker
```CMD
docker run --gpus all -it deepseek-gpu-docker /bin/bash
```


---

## Running Instructions

### Start Ollama
```bash
ollama start &
```


### Pull Model
```bash
ollama pull deepseek-r1:1.5b
```

### Run Model
```bash
ollama run deepseek-r1:1.5b
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
- `deepseek-r1:xb` **(replace x with parameter 1.5b, 7b, 8b, etc.)**
- `deepseek-r5`
- `deepseek-cos`  
- `deepseek-sin`  
- `deepseek-math`

To view all available models:
```bash
ollama list --model
```
