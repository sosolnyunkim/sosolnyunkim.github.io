---
layout: post
title:  "[Jetson Nano] Install Kernel"
date:   2022-12-17 00:00:00 +0000
image:  '/assets/img/JetsonNano.png'
tags:   [Setup]
---

### **1. 전체조건**

Jetson nano에는 이미 image가 설치되어 있어야 함. 


### **2. Kernel 설치하기**


##### 1) Kernel source code 다운 받기 및 압축 풀기

```shell 
wget https://developer.nvidia.com/embedded/l4t/r32_release_v5.1/r32_release_v5.1/sources/t210/public_sources.tbz2
tar -xvf public_sources.tbz2
cd Linux_for_Tegra/source/public
tar -xvf kernel_src.tbz2
```

##### 2) Configuration 파일 얻기

```shell
cd kernel/kernel-4.9
zcat /proc/config.gz > .config
```

##### 3) Kernel 컴파일하기

```shell
make menuconfig
make prepare && make modules_prepare && make -j4 Image && make -j4 modules
```

##### 4) Kernel 설치하기

```shell
sudo make modules_install && sudo cp arch/arm64/boot/Image /boot/Image
```

##### 5) Reboot 하기

```shell
sudo reboot
```
