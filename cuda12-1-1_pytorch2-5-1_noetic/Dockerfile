FROM nvidia/cuda:12.1.1-cudnn8-devel-ubuntu20.04
LABEL maintainer="HandianYang"

# Path settings
ARG USERNAME=developer
ENV HOME=/home/${USERNAME}

# ROS settings
ENV ROS_DISTRO=noetic
ENV ROS_ROOT=/opt/ros/${ROS_DISTRO}
ENV DEBIAN_FRONTEND=noninteractive

# Python and Pytorch settings
ARG PYTHON_VERSION=3.8
ARG TORCH_VERSION=2.5.1
ARG TORCH_VISION_VERSION=0.20.1
ARG TORCH_AUDIO_VERSION=2.5.1

# Install basic tools, Python, and pip
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
      # Python
      python3-pip \
      python${PYTHON_VERSION}-dev \
      # Basic tools
      build-essential \
      curl \
      git \
      gnupg2 \
      libffi-dev \
      libssl-dev \
      lsb-release \
      sudo \
      unzip \
      vim \
      wget && \
    rm -rf /var/lib/apt/lists/*

# Install ROS Noetic
RUN sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list' && \
    curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | apt-key add - && \
    apt-get update && \
    apt-get install -y --no-install-recommends \
      ros-${ROS_DISTRO}-desktop-full \
      python3-rosdep \
      python3-rosinstall \
      python3-rosinstall-generator \
      python3-wstool && \
    rosdep init || true && \
    rosdep update && \
    rm -rf /var/lib/apt/lists/*

RUN python3 -m pip install --upgrade \
      pip \
      setuptools \
      wheel && \
    # Pytorch
    pip install --no-cache-dir \
      torch \
      torchvision \
      torchaudio \
      --index-url https://download.pytorch.org/whl/cu121 && \
    # object detection & datasets
    pip install --no-cache-dir \
      gdown \
      pyrealsense2 \
      supervision && \
    # Detectron2
    pip install --no-cache-dir \
      ninja \
      --no-build-isolation 'git+https://github.com/facebookresearch/detectron2.git'

# Copy project files
WORKDIR ${HOME}
COPY . ${HOME}

# Set aliases and environment settings in .bashrc
RUN echo "" >> ${HOME}/.bashrc && \
    echo "source /opt/ros/${ROS_DISTRO}/setup.bash" >> ${HOME}/.bashrc && \
    echo "alias cm='catkin_make'" >> ${HOME}/.bashrc && \
    echo "alias sd='source devel/setup.bash'" >> ${HOME}/.bashrc && \
    apt-get clean

# NVIDIA settings
ENV NVIDIA_VISIBLE_DEVICES=all
ENV NVIDIA_DRIVER_CAPABILITIES=compute,utility
