# deepseek-gpu-docker

<h1>DeepSeek AI in a Docker Container with NVIDIA GPU Support</h1>
OverviewThis guide provides instructions for running DeepSeek AI in a Docker container with NVIDIA GPU support using Ollama.
PrerequisitesNVIDIA GPU with CUDA support
Docker
NVIDIA Container Toolkit
Ollama installed inside the container
Running DeepSeek AI in DockerStep 1: Build the Docker ImageEnsure you have a Dockerfile that includes the necessary dependencies, then build the image:
sudo docker build -t deepseek-gpu .Step 2: Run the Docker ContainerStart the container with GPU support:
docker run --gpus all -it deepseek-gpu /bin/bashStep 3: Verify GPU AvailabilityInside the container, verify that PyTorch can access the GPU:
python3 -c "import torch; print(torch.cuda.is_available())"If the output is True, your GPU is properly configured.
Step 4: Start OllamaInside the container, start the Ollama service:
ollama start &Step 5: Pull and Run DeepSeek AIDownload the DeepSeek model:
ollama pull deepseek-r1:1.5bRun the model:
ollama run deepseek-r1:1.5bAvailable DeepSeek AI Models and ParametersModel Variantsdeepseek-r1:1.5b - Lightweight model for general AI tasks
deepseek-r1:3b - Larger model with improved accuracy and comprehension
deepseek-r1:7b - High-performance model for complex AI applications
deepseek-r1:67b - Large-scale model for advanced deep learning tasks
Example UsagePulling and running different models:
ollama pull deepseek-r1:3b
ollama run deepseek-r1:3bCustomizing parameters when running:
ollama run deepseek-r1:7b --temperature 0.7 --top_k 50 --top_p 0.9NotesEnsure that your Docker image includes the necessary dependencies for PyTorch, CUDA, and Ollama.
If you encounter issues with GPU access, ensure that the NVIDIA Container Toolkit is properly installed and configured.
You may need to run docker commands with sudo depending on your system configuration.
TroubleshootingGPU not detected: Check if nvidia-smi works inside the container.
Ollama issues: Ensure that Ollama is installed and running before pulling the model.
LicenseThis setup follows the licensing terms of DeepSeek AI and Ollama. Ensure compliance with their respective licenses before use.
