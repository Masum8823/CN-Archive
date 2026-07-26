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

<a id="4-udp"></a>

## 4. UDP — User Datagram Protocol

### Definition
UDP (RFC 768) is a **"Best Effort"** transport protocol. It just sends data without checking if it arrived, without ordering it, and without any handshake. It's the scaled-down, no-frills version of TCP.

### Why Important?
Some apps (like video calls or online games) care more about **speed** than **perfection**. UDP exists exactly for these apps.

### Easy Explanation
Imagine sending postcards without registering them — you just drop them in the mailbox and hope they arrive. You don't get a receipt, you don't know the order they'll arrive in, and if one gets lost, nobody resends it. That's UDP.

**Why is UDP fast?**
- No connection setup delay (no handshake before sending)
- Small header size (only 8 bytes)
- No error control, no flow control, no congestion control — it just blasts data as fast as it can

### Key Points
- Connectionless & Unreliable
- No retransmission of lost data
- Smaller header → faster than TCP
- Favors **low latency** over **guaranteed delivery**

### Where is UDP used?
| Category | Examples |
|---|---|
| Streaming multimedia | Live video, live audio (loss-tolerant, speed-sensitive) |
| Network management | SNMP, DHCP, NTP |
| Naming service | DNS |
| Gaming | Online multiplayer games |
| Newer protocols | HTTP/3 (built on top of UDP, adds its own reliability) |

> **Note:** Even though DNS and HTTP/3 use UDP, they add their **own reliability at the application layer** — UDP itself still stays unreliable. This is called "reliable transfer over UDP."

### Shortcut Memory Trick
**UDP = Fast, Connectionless, Unreliable**
Remember: **"U Don't Promise"** (UDP doesn't promise delivery) 😄

### Exam Focus
- Why is UDP faster than TCP? (connection, header size, no control mechanisms)
- Name 4-5 real applications that use UDP
- DNS/HTTP3 exception — reliability added at application layer, not transport layer

---

<a id="5-segmentation-reassembly"></a>

## 5. Function 1 & 2 — Segmentation and Reassembly

### Definition
Before sending, Transport Layer breaks application data into small **pieces**, adds a **header** to each piece, and sends them out. On the receiving side, these pieces are **reassembled** back into the original data.

### Easy Explanation
Think of sending a big cake by post — you can't send the whole cake in one box, so you cut it into slices, put each slice in its own box with a label (header), and ship them. The receiver puts the slices back together using the labels.

- **UDP** → creates a **UDP Datagram** (Header + Piece)
- **TCP** → creates a **TCP Segment** (Header + Piece)

### Diagram (ASCII)
```
APPLICATION LAYER DATA
   [ Piece 1 ][ Piece 2 ][ Piece 3 ]

UDP Datagram:                     TCP Segment:
[Header][Piece 1]                 [Header][Piece 1]
[Header][Piece 2]                 [Header][Piece 2]
[Header][Piece 3]                 [Header][Piece 3]
```

### The Big Difference in Reassembly
| UDP (Connectionless & Unreliable) | TCP (Reliable) |
|---|---|
| Datagrams may take different routes and arrive **out of order** | Segments may take different routes but TCP **re-orders** them at destination |
| Out-of-order datagrams are **NOT re-ordered** | Segments are re-ordered using sequence numbers |
| Lost datagrams are **NOT re-sent** | Lost segments **are re-sent** |

### Remember
This is a classic exam diagram question: "Show how UDP vs TCP handle out-of-order delivery." UDP just delivers in whatever order it receives; TCP fixes the order.

### Exam Focus
- Draw/explain the difference in how UDP and TCP handle out-of-order segments/datagrams
- Key phrase: TCP **re-orders**, UDP does **not**

---

<a id="6-headers-overview"></a>

## 6. TCP and UDP Headers (Overview)

### Easy Explanation
Both protocols attach a header in front of the data before sending. But the header sizes are very different:

| Header | Size |
|---|---|
| **UDP Header** | Fixed **8 bytes** |
| **TCP Header** | **20 bytes minimum**, up to **60 bytes maximum** (with options) |

### UDP Header Fields (simple, only 4 fields)
```
| Source Port Number (16 bits) | Destination Port Number (16 bits) |
| Total Length (16 bits)       | Checksum (16 bits)                |
```

### TCP Header Fields (much more detailed — see section 11)
TCP header carries much more information because it needs to guarantee reliability: sequence numbers, acknowledgment numbers, control flags, window size, etc.

### Key Points
- UDP header = lightweight, 4 fields only
- TCP header = heavy, up to 10+ fields, because it must track connection state
- This size difference is **the main reason** UDP is faster than TCP

### Exam Focus
- Memorize exact header sizes: **UDP = 8 bytes fixed**, **TCP = 20–60 bytes**

---

<a id="7-ports-sockets"></a>

## 7. Function 3 — Ports and Sockets

### Definition
**Ports** identify which application/process on a computer should receive the data. A port number is **16 bits**, so it ranges from **0 to 65535**.

A **Socket** = **IP Address + Port Number** together. Example: `192.168.1.1:80`

### Why Important?
A computer usually has only **one IP address**, but it can run many applications at once (browser, Spotify, email). Ports let the Transport Layer know exactly which app the data belongs to.

### Easy Explanation
Think of an apartment building:
- The **building address** = IP Address
- Each **apartment/flat number** = Port Number
- The full delivery address (building + flat) = **Socket**

So when data arrives at your computer's IP, the port number tells it "go to apartment 443" (HTTPS) or "go to apartment 25" (Email/SMTP).

### Example
- **80** → Web/HTTP
- **25** → SMTP (Email)
- **4070** → Spotify

### Key Points
- Ports = 16-bit numbers (0–65535)
- Socket = IP Address : Port
- Because a computer has multitasking apps, ports keep everything separated

### Exam Focus
- Define Port and Socket clearly (short viva-type question)
- Be ready to write a socket example: `IP:Port`

---

<a id="8-port-types"></a>

## 8. Port Number Types

### Definition
Ports are divided into 3 categories based on their number range.

### Easy Explanation & Table

| Port Type | Range | Description |
|---|---|---|
| **Well-Known Ports** | 0 – 1023 | Assigned & controlled by **IANA**, used by standard services |
| **Registered Ports** | 1024 – 49,151 | Registered by IANA for specific vendor apps (not as strict as well-known) |
| **Dynamic (Private/Ephemeral) Ports** | 49,152 – 65,535 | Never assigned by IANA, used temporarily by clients |

> Total available ports in TCP/IP = **65,536**

### Well-Known Ports (memorize these!)
| Port | Service |
|---|---|
| 25 | SMTP |
| 53 | DNS |
| 67 & 68 | DHCP |
| 80 | HTTP |
| 110 | POP3 |
| 123 | NTP |
| 143 | IMAP |
| 443 | HTTPS |

### Registered Ports (examples)
| Port | Service |
|---|---|
| 3306 | MySQL |
| 4070 | Spotify |
| 5060 | SIP (VoIP) |
| 8008 / 8080 | Alternate HTTP |
| 23399 | Skype |

### Dynamic Ports
- Also called **private** or **ephemeral** ports
- Used by client applications as a **temporary source port** when connecting to a server
- Some systems (older Linux kernels, some enterprise firewalls) use the **32768 to 61000** sub-range specifically for these

### Shortcut Memory Trick
**"0 to 1023 = Well Known, Others are Not"** — just remember 1023 as the cutoff, and everything above splits into Registered (up to ~49k) and Dynamic (rest).

### Exam Focus
- Memorize the three ranges exactly: 0-1023, 1024-49151, 49152-65535
- Memorize well-known ports table (very high chance in MCQ/short questions)

---


<a id="9-ports-in-action"></a>

## 9. Port Numbers in Action

### Easy Explanation
Let's say you open `www.cisco.com` in your browser.

**Step 1 — Client sends a request:**
- Source Port = `49650` (a random dynamic port your browser picked)
- Destination Port = `80` (server listens here for HTTP)

**Step 2 — Server replies:**
- Source Port = `80` (server's own port)
- Destination Port = `49650` (sends it back to exactly where the request came from)

### Why can't servers use random ports?
- **Clients** can use any random (dynamic) port — no problem, because the client already knows who it's talking to.
- **Servers** must use a fixed, **well-known port number** — otherwise, clients won't know where to send their request in the first place!

### What if you open 2 tabs to the same website?
Each tab gets a **different dynamic source port** (e.g., 49650 and 49655), even though the destination is the same (port 80). This keeps the two browser sessions separate on the server side.

### How does the server tell sessions apart?
Using the **socket** — the full combination of IP + Port:
```
172.16.230.5:49650  <-->  207.22.146.33:80   (Tab 1 / PC 1)
172.16.230.6:49650  <-->  207.22.146.33:80   (PC 2, same port but different IP)
```
Since the socket includes the IP address too, even if two different PCs use the same source port number, the server can still tell them apart.

### Tool: Netstat
`netstat -a -n` command shows active connections on your PC — Source IP, Source Port, Destination IP, Destination Port, and Connection State (LISTENING, ESTABLISHED, TIME_WAIT, etc.)

### Exam Focus
- Explain why servers must use well-known ports but clients don't
- Explain how sockets keep multiple sessions separate
- `netstat -a -n` command usage might appear in viva

---

<a id="10-mux-demux"></a>

## 10. Function 4 — Multiplexing & Demultiplexing

### Definition
**Multiplexing**: Combining data from multiple applications (Skype, browser, Netflix) into a single stream to send over the network.

**Demultiplexing**: On the receiving end, splitting that single incoming stream back out to the correct applications.

### Easy Explanation
Think of a highway:
- **Multiplexing** = many cars from different roads merging into one highway
- **Demultiplexing** = cars exiting the highway at different exits to reach their own destinations

### How is demultiplexing decided?
| Protocol | Demultiplexing uses |
|---|---|
| **UDP** | Destination port number **only** |
| **TCP** | **4-tuple**: Source IP, Destination IP, Source Port, Destination Port |

### Key Points
- TCP needs more information (4-tuple) because it must track each individual **connection**, not just the port
- UDP is simpler — it only cares about which port the data should go to

### Exam Focus
- Difference in demultiplexing: UDP (port only) vs TCP (4-tuple) — **very common exam question**

---

<a id="11-tcp-header-detailed"></a>

## 11. TCP Segment Header (Detailed)

### Definition
The TCP header is much bigger and more detailed than UDP's because TCP has to guarantee reliable, ordered delivery.

### Diagram (ASCII layout)
```
| Source Port (16)         | Destination Port (16)      |
| Sequence Number (32 bits)                              |
| Acknowledgment Number (32 bits)                        |
| HLEN(4) | Reserved(6) | Flags(6) | Window Size (16)     |
| Checksum (16)             | Urgent Pointer (16)        |
| Options and Padding (0–40 bytes)                        |
```

### Key Points
- Total header size: **20 bytes minimum, 60 bytes maximum**
- Extra size compared to UDP mostly comes from Sequence Number, Ack Number, Flags, and Options

### Exam Focus
- Draw the TCP header layout from memory
- Know each field's **bit size** (this is commonly asked)

---