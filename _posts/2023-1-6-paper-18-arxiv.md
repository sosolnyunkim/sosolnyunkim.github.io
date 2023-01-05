---
layout: post
title:  "[Paper] Real-time Linux communications: an evaluation of the Linux communication stack for real-time robotic applications"
date:   2023-01-06 00:00:00 +09:00
image:  '/assets/img/arxiv2.png'
tags:   [Paper]
---

### Paper Info
Gutiérrez, C. S. V., Juan, L. U. S., Ugarte, I. Z., & Vilches, V. M. (2018). Real-time Linux communications: an evaluation of the Linux communication stack for real-time robotic applications. arXiv preprint arXiv:1808.10821  

***

### **Summary**
This paper provides a **deterministic network latency** on the UDP protocol by an **appropriate configuration**. First, they show that there is a high number of deadline miss and a high maximum latency on a vanilla kernel and PREEMPT-RT kernel. Second, they set the affinity of all the IRQ thread, the client and the server application to same CPU. They show the network latency is bounded and there are no deadline misses. Third, they set the affinity of all the IRQs to the non real-time CPU, while the IRQs of the real-time are set with affinity in the isolated CPU.

***

### **Detail**
본 논문에서는 configuration에 따른 network latency와 deadline miss의 수의 변화가 중요함. 따라서 각 configuration에 대한 설명과 결과에 대해서 설명함.
##### 1) Setup
2개의 device를 사용하여 실험을 진행함. 하나의 device에서는 client application이 실행되고, 다른 하나의 device에서는 server application이 실행됨. client application은 UDP packet을 1ms당 500byte를 전송함. 이때 network latency는 t2-t1를 의미함. 
![](/assets/img/18-arxiv.png)
##### 2) Configuration
###### (1) Vanilla kernel 
Real-time이 아닌 default kernel 환경을 의미함.  
Server와 client만 data를 주고받는 상황에서조차 높은 deadline miss 수와 높은 최대 latency가 측정됨.  
당연히 CPU, memory, network load가 많은 상황에서는 더 심화됨.
###### (2) PREEMPT-RT kernel with any CPU
Real-time kernel인 PREEMPT-RT kernel 환경임. 이때 network IRQ, client application, server application은 모두 아무 CPU에서 실행될 수 있음.  
server와 client만 data를 주고받는 상황과 CPU, memory load가 많은 상황에서는 latency가 bound됨.  
그러나, network load가 많은 상황에서는 여전히 latency가 증가되고, deadline miss가 발생함.
###### (3) PREEMPT-RT kernel with binding CPU 
Real-time kernel인 PREEMPT-RT kernel 환경임. network IRQ, client application, server application은 모두 각 device의 CPU 1번에서만 실행됨.  
모든 상황에서 latency가 bound되고, deadline miss가 발생하지 않음.
###### (4) PREEMPT-RT kernel with isolationi
Real-time kernel인 PREEMPT-RT kernel 환경임. real-time application에 관련된 thread (IRQ & application)만 하나의 CPU에서 실행함. 그 외의 non real-time application에 관련된 모든 thread는 다른 CPU에서 실행함.  
3번 환경과 동일한 결과가 나옴.  
궁금한 점: 3번 환경과의 결과가 비교했을 때, 달라지는 점이 없는데 왜 이 방법을 제시했는지 모르겠음.
##### 3) Conclusion
UDP protocol에서 real-time application을 실행할 때, 적절한 configuration을 사용하면 bound된 latency와 no deadline miss를 가질 수 있음.











