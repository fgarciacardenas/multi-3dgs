# Dockerfile
# Accept BASE_IMAGE as a build argument with a default value
ARG BASE_IMAGE=pytorch/pytorch:2.2.1-cuda11.8-cudnn8-devel
FROM ${BASE_IMAGE}

# Set environment variable to prevent interactive prompts during package installation
ENV DEBIAN_FRONTEND=noninteractive

# Install APT packages including Python and pip
RUN apt-get update && apt-get install -y \
    # Ubuntu essentials    
    cmake \
    build-essential \
    sudo \
    rsync \
    wget \
    unzip \
    git-all \
    # Python essentials
    python3 \
    python3-pip \
    python3-venv \
    python3-tk \
    # Libraries for X11 visualization
    libx11-dev \
    libxrender1 \
    libxext6 \
    libfontconfig1 \
    # Other dependencies
    libglib2.0-0 \
    # Remove cached data
    && rm -rf /var/lib/apt/lists/*

# Upgrade pip to the latest version (optional but recommended)
RUN pip3 install --upgrade pip

# Install Python packages
RUN pip3 install --no-cache-dir \
    opencv-python \
    ipython \
    pytorch-lightning \
    #scikit-learn \
    #matplotlib \
    #pandas \
    tqdm

# Add Build Arguments for UID and GID
# ARG USER_NAME=devuser
# ARG USER_ID=1000
# ARG GROUP_ID=1000

# Create a group with the same GID as the host
# RUN groupadd --gid ${GROUP_ID} ${USER_NAME} || echo "Group ${USER_NAME} already exists"

# Create a user with the specified UID and GID
# RUN useradd --uid ${USER_ID} --gid ${GROUP_ID} --shell /bin/bash --create-home ${USER_NAME}

# Add passwordless sudo for devuser
# RUN echo "${USER_NAME} ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/${USER_NAME} && \
#     chmod 0440 /etc/sudoers.d/${USER_NAME}

# Set the working directory
#WORKDIR /home/${USER_NAME}/project

# Switch to the non-root user
#USER ${USER_NAME}

# Add /home/devuser/.local/bin to PATH
#ENV PATH=/home/${USER_NAME}/.local/bin:${PATH}

# Set DISPLAY variable
ENV DISPLAY=:0