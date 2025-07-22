RUN apt-get update && apt-get install -y \
    build-essential \
    git \
    curl \
    libgl1-mesa-glx \
    libsm6 \
    libxext6 \
    libxrender1 \
    && rm -rf /var/lib/apt/lists/*

# Set working directory
WORKDIR /workspace/FinRL

# Copy requirements.txt first to leverage Docker caching
COPY requirements.txt .

# Install Python dependencies (TensorFlow, PyTorch, etc.)
# Using --no-cache-dir to keep the image size down
# This step will be part of the prebuild, making workspace startup faster
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the application code
COPY . .

# Expose ports if FinRL services run on specific ports (e.g., Jupyter)
EXPOSE 8888

# Command to run when the container starts (optional, postStartCommand in devcontainer.json is often preferred)
# CMD ["bash"]

