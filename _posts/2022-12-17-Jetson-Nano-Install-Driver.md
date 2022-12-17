---
layout: post
title:  "[Jetson Nano] Install Driver"
date:   2022-12-17 00:00:00 +09:00
image:  '/assets/img/JetsonNano2.png'
tags:   [Setup, Jetson Nano]
---

### **1. 전제조건**
Jetson Nano에는 kernel이 이미 설치되어 있어야 함.

### **2. Driver 확인하기**

##### Jetson Nano에서 driver 확인하기

```shell
ethtool -i eth0
```

![](/assets/img/JetsonNano_driver.png)

### **3. Driver 설치하기**


##### 1) 아래의 파일에서 r8168 driver code 다운 받기

<a href="/assets/file/0009-r8168-8.044.02.tar.bz2">0009-r8168-8.044.02.tar.bz2</a>


##### 2) 다운받은 파일 풀기


```shell
tar vjxf 0009-r8168-8.044.02.tar.bz2
```

##### 3) Driver 모듈 컴파일하기

```shell
cd r8168-8.044.02
sudo make clean modules
sudo make -j4
```

##### 4) Kernel에서 built-in 모듈이 아닌 다운받은 모듈을 사용할 수 있도록 변경해주기

(1) 아래의 command를 실행하면 그림과 같이 나타남

```shell
cd Linux_for_Tegra/source/public/kernel/kernel-4.9
make menuconfig
```

![](/assets/img/JetsonNano_driver2.png)

(2) "/r8168"을 치면 아래와 그림과 같이 나타남. "ok"를 누르면 됨.

![](/assets/img/JetsonNano_driver3.png)

(3) "1" 누르고, 아래 그림과 같이 "M"으로 바꿔주면 다운받은 모듈을 사용할 수 있음.

![](/assets/img/JetsonNano_driver4.png)

##### 5) Kernel 컴파일하기

```shell
make prepare && make modules_prepare && make -j4 Image && make -j4 modules 
sudo make modules_install && sudo cp arch/arm64/boot/Image /boot/Image
sudo reboot
```

##### 6) 기존의 built-in driver를 rmmod한 후, 설치한 모듈을 insmod하기

```shell
sudo rmmod r8168 && sudo insmod ./src/r8168.ko
```
