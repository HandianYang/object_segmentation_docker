# `object-segmentation:cuda12.1.1-pytorch2.5.1-noetic`

## Prerequisites
+ Hardware:
  - GPU: any CUDA 12.1-capable (RTX 3060 Ti or better)
  - RealSense: D435 or D435i
+ Software:
  - GPU driver: >= 525.60
  - Docker: >= 20.10
  - NVIDIA Container Toolkit (`nvidia-docker2`)

## Base image: `nvidia/cuda:12.1.1-cudnn8-devel-ubuntu20.04`

## Crucial packages
* ROS Noetic
* CUDA 12.1.1
* Pytorch 2.5.1
* Detectron2 (instance segmentation)

## Tools and dependencies
* Common tools:
  - `build-essential`
  - `curl`
  - `git`
  - `gnupg2`
  - `libffi-dev`
  - `libssl-dev`
  - `lsb-release`
  - `sudo`
  - `unzip`
  - `vim`
  - `wget`
* Python3.8 tools:
  - `python3.8-dev`
  - `python3-pip`
* Dependencies for ROS building packages
  - `python3-rosdep`
  - `python3-rosinstall`
  - `python3-rosinstall-generator`
  - `python3-wstool`
* Dependencies for object segmentation (installed through `pip`)
  - `gdown`
  - `ninja`
  - `pyrealsense2`
  - `setuptools`
  - `supervision`
  - `wheel`

## Other features

### Alias
* `cm`: `catkin_make`
* `sd`: `source devel/setup.bash`
