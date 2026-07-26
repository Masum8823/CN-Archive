# 🌐 Transport Layer (TCP & UDP) — Complete Exam Notes

![Course](https://img.shields.io/badge/Course-Data%20Communications%20(CSE%203227)-blue)
![Topic](https://img.shields.io/badge/Chapter-Transport%20Layer-green)
![Level](https://img.shields.io/badge/Level-Exam%20Ready-orange)
![Made%20with](https://img.shields.io/badge/Made%20with-%E2%9D%A4%EF%B8%8F%20Easy%20English-red)

> This README covers the complete **Transport Layer chapter** — TCP, UDP, ports, sockets, headers, sequence/acknowledgment numbers, multiplexing, and the 3-way handshake. Read this once before exam, and you won't need to open the slides again.

---

## 📑 Table of Contents

* [1. Introduction to Transport Layer](#1-introduction)
* [2. Transport Layer vs Network Layer](#2-transport-vs-network)
* [3. Functions of the Transport Layer](#3-functions)
* [4. UDP — User Datagram Protocol](#4-udp)
* [5. Function 1 & 2 — Segmentation and Reassembly](#5-segmentation-reassembly)
* [6. TCP and UDP Headers (Overview)](#6-headers-overview)
* [7. Function 3 — Ports and Sockets](#7-ports-sockets)
* [8. Port Number Types](#8-port-types)
* [9. Port Numbers in Action](#9-ports-in-action)
* [10. Function 4 — Multiplexing & Demultiplexing](#10-mux-demux)
* [11. TCP Segment Header (Detailed)](#11-tcp-header-detailed)
* [12. Byte Number & Sequence Number](#12-sequence-number)
* [13. Acknowledgment Number](#13-ack-number)
* [14. Header Length, Control Bits, Window Size](#14-hlen-control-window)
* [15. Checksum, Urgent Pointer, Options](#15-checksum-urgent-options)
* [16. TCP Connection Establishment (3-Way Handshake)](#16-three-way-handshake)
* [17. TCP Data Transfer & Connection Termination](#17-data-transfer)
* [18. TCP vs UDP — Full Comparison](#18-tcp-vs-udp)
* [19. Quick Revision (Whole Chapter)](#19-quick-revision)
* [20. Important Port Numbers (Table)](#20-important-ports)
* [21. Frequently Asked Exam Questions](#21-faq)
* [22. Common Mistakes](#22-common-mistakes)
* [23. Memory Tricks](#23-memory-tricks)
* [24. Exam Tips](#24-exam-tips)

---

<a id="1-introduction"></a>

## 1. Introduction to Transport Layer

### Definition
The **Transport Layer** is the layer that handles communication **between processes/applications** running on two different hosts. It's not about connecting computers — it's about connecting the actual *apps* running inside those computers (like your browser talking to a web server's app).

### Why Important?
Every network exam has at least one question from this chapter. It's the foundation for understanding how apps like browsers, games, and video calls actually send and receive data reliably (or quickly).

### Easy Explanation
Think of two houses — **Ann's house** and **Bill's house**. Inside each house, there are **12 kids**. Each kid wants to send letters to a specific kid in the other house.

* **Kids** = Processes (applications)
* **Letters in envelopes** = Application messages
* **Houses** = Hosts (computers)
* **Ann and Bill** = Transport Layer protocol (they make sure the right letter reaches the right kid inside the house)
* **Postal Service** = Network Layer protocol (it just delivers things house to house, doesn't care which kid)

So:
- **Network Layer** → host to host (house to house) communication
- **Transport Layer** → process to process (kid to kid) communication

The data unit at this layer is called a **Segment** (for TCP) — this is the Transport Layer's own version of a "packet".

### Key Points
- Transport Layer = logical communication between **processes**
- Network Layer = logical communication between **hosts**
- Two main protocols: **UDP** and **TCP**
- Data unit (PDU) of Transport Layer = **Segment**

### Exam Focus
- Difference between Transport layer and Network layer (very common question)
- The household analogy might come as a short question — understand it, don't just memorize it

---

<a id="2-transport-vs-network"></a>

## 2. Transport Layer vs Network Layer

### Easy Explanation
| Transport Layer | Network Layer |
|---|---|
| Talks between **processes** (apps) | Talks between **hosts** (devices) |
| Example: Chrome talking to a web server app | Example: Your PC talking to the destination server machine |
| Analogy: Ann & Bill sorting letters for the right kid | Analogy: Postal service delivering between houses |

### Remember
If a question asks "what's the difference between transport and network layer" — always mention **process-to-process vs host-to-host**. This is the #1 keyword examiners look for.

---

<a id="3-functions"></a>

## 3. Functions of the Transport Layer

### Definition
The Transport Layer has several core jobs. Some are done by **both TCP and UDP**, and some are done **only by TCP** (because TCP is the "reliable" one).

### Easy Explanation
Here are all 7 functions:

1. **Segmenting the data** and managing each piece
2. **Reassembling** the segments back into a stream of application data
3. **Identifying the different applications** (using port numbers)
4. **Multiplexing** (combining multiple app data into one line for sending)
5. **Establishing and terminating a session/connection**
6. **Enabling error recovery** (only TCP does this properly)
7. **Performing flow control** between end users (only TCP)

### Key Points
| Function | Done by |
|---|---|
| Segmentation & Reassembly | UDP & TCP |
| Identifying Applications (Ports) | UDP & TCP |
| Multiplexing | UDP & TCP |
| Connection Establishment & Termination | **Only TCP** |
| Error Recovery / Control | **Only TCP** |
| Flow Control | **Only TCP** |

### Remember
This "Only TCP" vs "Both" distinction is a favorite viva/MCQ question. TCP does extra work because it promises **reliability**; UDP skips these to stay **fast**.

### Exam Focus
- List the 7 functions
- Mark which ones are TCP-only
- Be ready to explain *why* TCP needs connection setup but UDP doesn't

---