---
layout: ../../layouts/BlogLayout.astro
title: 'Define Computer'
pubDate: '2024-01-21 20:09'
blurb: 'Where Assembly Language fits in'
tags: ["lecture","cs321"]
---

## Main Points

- [[#Define a Computer]]
- [[#Language to Hardware]]
- [[#Memory]]
- [[#Communicating with other Computers]]

# Define a Computer

> [!tip] Computer
> There are 5 main components that make up a computer: Input, Output, Memory, Dataflow, Control. 
> Dataflow and Control are usually grouped and referred to as the processor

Every component of a computer can be categorized to one of the groups in the following image:

![[Pasted image 20240122015403.png]]

The most common and interesting I/O device is the graphics display. It renders an *image*, which is a matrix composed of *picture elements* (pixels), where each pixel corresponds to a transistor that controls the light display.  The pixels can be represented as a matrix of bits, called a **bit map**, which is used to control the transistor at each pixel location on the display, and each pixel can have multiple bits to display millions of different colors. 

The computer uses a **frame buffer** to store the bit map; the image to be represented onscreen is stored in the frame bugger, and the bit pattern per pixel is read out to the graphics display at the refresh rate. The goal of the bit map is to represent faithfully what is on the screen. 

![[Pasted image 20240122015942.png]]

The ***processor*** 

---
# Language to Hardware

[[Computing Principiles#Abstraction|Abstraction]] is such an important idea because of how difficult programming becomes when dealing with hardware and the lowest levels of software. In order to make things easier, abstraction is *necessary* because it enables computer designers to focus on *functions* rather than *hardware*. 


> [!def] Instruction Set Architecture
> The abstraction layer between the hardware and lowest level software is so important that it is given its own name: ***Instruction Set Architecture***. 
> The instruction set architecture includes anything programmers need to know to make a binary machine language program work correctly, including instruction, I/O devices, and so on. 


>**Ex.)** We can talk about the functions of a digital clock (keeping time, displaying the time, setting the alarm) separately from the clock hardware (quartz crystal, LED, plastic buttons).  

An ***Implementation*** is hardware that obeys an architecture abstraction.



> [!fact] Big Idea
> Both Hardware and software consist of hierarchical layers using abstraction, with each lower layer hiding details from the level above. One key interface between the levels of abstraction is the *instruction set architecture* -- the interface between the hardware and low-level software. This abstract interface enables many *implementations* of varying cost and performance to run identical software.

---
# Memory

There are 2 types of memory: 
- Volatile $\to$ when it loses power, it forgets
- Nonvolatile $\to$ persists

To distinguish between the volatile memory used to hold data and programs while they are running and this *nonvolatile* memory used to store data and programs between runs, the term **primary/main memory** is used for running programs, and **secondary memory** for storage.

---
# Communicating with other Computers

Computer networks interconnect whole computers, allowing users to extend the power of computing by including communication.

Networks have several main advantages:
- **Communication**: Information is exchanged between computers at high speeds
- **Resource sharing**: Rather than each computer having its own I/O devices, computers on the network can share I/O devices
- **Nonlocal access**: By connecting computers over logn distances, users need not be near the computer they are using

Networks vay in length and performance, and the cost of communication increases according to speed and distance the information travels.

The most popular connection type being *ethernet*, which is an example of **Local Area Network (LAN)**, which constract to **Wide Area Networks** which cross continents and are the backbone of the Internet, which are usually connected with fiber optic cables. 

***Wireless technology*** has only been around for the past decade, which has enabled **Personal Mobile Devices (PMDs)** to exist and flourish. More recent innovations in radio are used for memory and microprocessors enabled significant improvement in price. 



---
