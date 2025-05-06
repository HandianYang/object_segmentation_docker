Version 1.0.1 (May 6, 2025)
----------------------------

+ Installed `gdown` for fetching datasets and model weights from Google Drive

Version 1.0.0 (May 5, 2025)
----------------------------

+ Built from `nvidia/cuda:12.1.1-cudnn8-devel-ubuntu20.04`
+ Installed crucial packages:
  - ROS Noetic
  - CUDA 12.1.1
  - Pytorch 2.5.1
  - Detectron2 (instance segmentation)
+ Added `nvidia-` and `libnvidia-` packages to `Unattended-Upgrade::Package-Blacklist {}`
+ Added aliases:
  - `cm = catkin_make`
  - `sd = source devel/setup.bash`
