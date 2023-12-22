---
title: Systems and Networks
date: 2022-04-25
tags: [
    "c", "assembly",
]
---

Overview of computer system structure and networking, covering aspects such as processor organization, memory hierarchy, storage devices, parallel processors, networking hardware, software abstractions in operating systems, and networking protocols, with a focus on orchestrating the efficient utilization of computing resources.
<!--more-->
## [Project 1](https://github.com/le-que/Systems-and-Networks/tree/main/cs2200-project1)
* Phase 1 - Implement the Datapath
* Phase 2 - Implement the Microcontrol Unit
* Phase 3 - Microcode and Testing

![static](/img/post/lc22.png)
##### LC-22a

![static](/img/post/microcontroller.png)
##### Microcontroller

![static](/img/post/CmpReg.png)
##### Compare Register

![static](/img/post/alu.png)
##### ALU

![static](/img/post/PC.png)
##### Program Counter

![static](/img/post/ram.png)
##### RAM

## [Project 2](https://github.com/le-que/Systems-and-Networks/tree/main/cs2200-project2)
* Phase 1 - Implementing a Basic Interrupt
* Phase 2 - Implementing Interrupts from Input Devices
    * Monitor the temperature of bread in a toaster, recording the highest and lowest temperatures, and calculating the temperature difference at memory address 0xFFFE.

![static](/img/post/Interrupt.png)
##### Interrupt

![static](/img/post/timer.png)
##### Timer

![static](/img/post/toaster.png)
##### Toaster

## [Project 3](https://github.com/le-que/Systems-and-Networks/tree/main/cs2200-project3)
This project involves completing a virtual memory system simulator by implementing crucial components such as virtual address breakdown, system and memory access bookkeeping, process initialization, page fault handling, frame eviction algorithms (FIFO and Clock Sweep), and calculating the Average Memory Access Time (AMAT) through modifications in specific files. 

## [Project 4](https://github.com/le-que/Systems-and-Networks/tree/main/cs2200-project4)
The given task involves implementing three CPU scheduling algorithms: First Come, First Serve (FCFS), which is non-preemptive; Round-Robin, which is preemptive and assigns time slices to processes; and Preemptive Priority (PS), where processes with higher priority are scheduled first, with preemptive behavior for higher-priority processes.

## [Project 5](https://github.com/le-que/Systems-and-Networks/tree/main/cs2200-project5)
This project involves a comprehensive exploration of network layers, with a focus on enhancing the reliability of the transport layer in a simulated network. Participants will delve into thread usage in operating systems, examine message segmentation and reassembly, implement the stop-and-wait protocol with acknowledgments and retransmissions, incorporate a checksum, and ultimately design a new Reliable Transport Protocol (RTP) for secure communication between a client and server, where encrypted messages are exchanged and decrypted responses are printed.