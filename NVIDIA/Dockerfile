# Use NVIDIA CUDA 12.8 with cuDNN and Ubuntu 24.04
FROM nvidia/cuda:12.8.0-cudnn-devel-ubuntu24.04

# Set environment variables
ENV DEBIAN_FRONTEND=noninteractive \
    PATH=/usr/local/cuda/bin:$PATH \
    LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH

# Install dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    python3 python3-venv python3-pip \
    git curl wget ca-certificates \
    libstdc++6 libopenblas-dev \
    && rm -rf /var/lib/apt/lists/*

# Create a virtual environment and activate it
RUN python3 -m venv /opt/venv
ENV PATH="/opt/venv/bin:$PATH"

# Upgrade pip inside the virtual environment
RUN pip install --upgrade pip

# Install PyTorch with CUDA
RUN pip install --no-cache-dir \
    torch torchvision torchaudio \
    --index-url https://download.pytorch.org/whl/cu121

# Install DeepSeek dependencies
RUN pip install --no-cache-dir deepseek-coder

# Install Ollama
RUN curl -fsSL https://ollama.com/install.sh | sh

# Set working directory
WORKDIR /app

# Default command
CMD ["/bin/bash"]
