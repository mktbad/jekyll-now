---
layout: post
title: NVIDIA Graphics Driver + Docker + NVIDIA Container Toolkit
category: setup
---

# Docker
[ref(graphics driver & docker & nvidia container toolkit)](https://blog.amedama.jp/entry/docker-nvidia-container-toolkit)

[ref2(nvidia container toolkit)](https://7me.oji.0j0.jp/2019/11/07/docker19-enable-nvidia-gpu/)

[doker公式](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

[nvidia container toolkit公式](https://github.com/NVIDIA/nvidia-docker)

``` console
#graphics driver
#do enroll mok
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt -y install ubuntu-drivers-common
sudo ubuntu-drivers autoinstall

#docker 
sudo apt -y install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt update
sudo apt-get install -y docker-ce docker-ce-cli containerd.io
sudo docker version

#nvidia container toolkit
distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | sudo apt-key add -
curl -s -L https://nvidia.github.io/nvidia-docker/$(. /etc/os-release;echo $ID$VERSION_ID)/nvidia-docker.list | sudo tee /etc/apt/sources.list.d/nvidia-docker.list
sudo apt update
sudo apt install -y nvidia-container-toolkit
sudo systemctl restart docker
```

``` console
# CUDA + CUDNN
sudo docker pull nvidia/cuda:10.1-cudnn7-devel-ubuntu18.04
# Pytorch
sudo docker pull pytorch/pytorch:1.3-cuda10.1-cudnn7-devel
# Base run
sudo docker run \
    --name bbb \
    --gpus all \
    -v ~/docker/bbb/:/root/host/ \
    -it aaa \
    bash
```
