<div align="center">

# 🌐 OSI Model & TCP/IP Model

### Computer Network — Networking Fundamentals
 
![Topic](https://img.shields.io/badge/Topic-Networking-blue?style=flat-square)
![Layers](https://img.shields.io/badge/OSI-7%20Layers-orange?style=flat-square)
![Layers](https://img.shields.io/badge/TCP%2FIP-4%20Layers-green?style=flat-square)
![Status](https://img.shields.io/badge/Status-Exam%20Ready-success?style=flat-square)
 
</div>

 
## 📑 Table of Contents
- [🌐 OSI Model (7 Layers)](#osi-model-7-layers)
- [🔟 OSI Layers Explained](#osi-layers-explained)
  - [Layer 7 — Application](#layer-7-application)
  - [Layer 6 — Presentation](#layer-6-presentation)
  - [Layer 5 — Session](#layer-5-session)
  - [Layer 4 — Transport](#layer-4-transport)
  - [Layer 3 — Network](#layer-3-network)
  - [Layer 2 — Data Link](#layer-2-data-link)
  - [Layer 1 — Physical](#layer-1-physical)
- [🔄 How OSI Layers Work Together](#how-osi-layers-work-together)
- [📶 TCP/IP Model](#tcpip-model)
- [⚖️ OSI vs TCP/IP](#osi-vs-tcpip)
- [✉️ Example: Sending an Email](#example-sending-an-email)
- [🎯 Exam Tips](#exam-tips)
---

<a id="osi-model-7-layers"></a>

## 🌐 OSI Model (7 Layers)
 
> The **OSI (Open Systems Interconnection) Model** is a framework that explains how data travels from one device to another through a network. It has **7 layers**, and each layer performs a specific task.
 
### OSI Layers (Top → Bottom)
 
| Layer | Name | Main Function |
|:---:|:---|:---|
| 7 | 🖥️ Application | Provides network services to users and applications |
| 6 | 🔐 Presentation | Translates, compresses, and encrypts data |
| 5 | 🔄 Session | Establishes, manages, and terminates communication sessions |
| 4 | 🚚 Transport | Provides end-to-end communication and reliability |
| 3 | 🗺️ Network | Handles logical addressing and routing |
| 2 | 🔗 Data Link | Provides communication between devices on the same network |
| 1 | ⚡ Physical | Transmits raw bits through cables or wireless signals |
 
---

<a id="osi-layers-explained"></a>

## 🔟 OSI Layers Explained
 
<a id="layer-7-application"></a>

#### Layer 7: Application Layer
 
<details>
<summary><b>📖 Click to expand details</b></summary>

The **Application Layer** is the closest layer to the user. It allows applications to access network services.
 
**Functions**
- Provides services to user applications
- Supports web browsing, email, and file transfer
- Acts as the interface between software and the network
**Examples**
- HTTP (Web)
- HTTPS (Secure Web)
- SMTP (Email)
- FTP (File Transfer)

</details>

<a id="layer-6-presentation"></a>

#### Layer 6: Presentation Layer
 
<details>
<summary><b>📖 Click to expand details</b></summary>

The **Presentation Layer** ensures that data is in a format both devices can understand.
 
**Functions**
- Data translation
- Data compression
- Data encryption and decryption
- Character encoding

**Examples**
- SSL/TLS
- JPEG
- ASCII
- Unicode

</details>

<a id="layer-5-session"></a>

#### Layer 5: Session Layer
 
<details>
<summary><b>📖 Click to expand details</b></summary>

The **Session Layer** manages communication sessions between applications.
 
**Functions**
- Starts communication sessions
- Maintains active sessions
- Ends sessions properly
- Provides synchronization and checkpoints

**Example**
- Video conferences
- Online meetings
- Long file transfers

</details>

<a id="layer-4-transport"></a>

#### Layer 4: Transport Layer
 
<details>
<summary><b>📖 Click to expand details</b></summary>

The **Transport Layer** provides reliable communication between sender and receiver.
 
**Functions**
- Segmentation and reassembly
- Error control
- Flow control
- Port addressing
- End-to-end delivery

**Protocols**
| Protocol | Description |
|:---|:---|
| **TCP** (Transmission Control Protocol) | Reliable and connection-oriented |
| **UDP** (User Datagram Protocol) | Faster but connectionless |
 
**PDU:** `Segment`
 
</details>

<a id="layer-3-network"></a>

#### Layer 3: Network Layer
 
<details>
<summary><b>📖 Click to expand details</b></summary>

The **Network Layer** is responsible for routing data between different networks.
 
**Functions**
- Logical addressing
- Path determination
- Routing packets
- Network-to-network delivery

**Protocol:** IP (Internet Protocol)
 
**PDU:** `Packet`
 
</details>

<a id="layer-2-data-link"></a>

#### Layer 2: Data Link Layer
 
<details>
<summary><b>📖 Click to expand details</b></summary>

The **Data Link Layer** provides communication between devices connected to the same network.
 
**Functions**
- Framing
- MAC addressing
- Error detection
- Flow control
- Media access control
**Example:** Ethernet
 
**MAC Address:** Data Link Layer identifier
 
**PDU:** `Frame`
 
</details>

<a id="layer-1-physical"></a>

#### Layer 1: Physical Layer
 
<details>
<summary><b>📖 Click to expand details</b></summary>

The **Physical Layer** is responsible for transmitting raw bits through a physical medium.
 
**Functions**
- Signal transmission
- Cable and connector management
- Bit synchronization
- Transmission modes

**Transmission Modes**
- Simplex
- Half-Duplex
- Full-Duplex

**PDU:** `Bits`
 
</details>

---

<a id="how-osi-layers-work-together"></a>

## 🔄 How OSI Layers Work Together
 
> When data is sent from one device to another:
 
```text
1. Data starts at the Application Layer.
2. It moves downward through all layers.
3. Each layer adds its own information (Encapsulation).
4. Data travels through the network.
5. At the receiver side, layers remove the added information (Decapsulation).
6. The original message reaches the destination application.
```
 
---

<a id="tcpip-model"></a>

## 📶 TCP/IP Model
 
> The **TCP/IP Model** is the practical networking model used on the Internet. It contains **4 layers**.
 
### TCP/IP Layers (Top → Bottom)
 
| Layer | Function |
|:---|:---|
| 🖥️ Application | User services and network applications |
| 🚚 Transport | End-to-end communication |
| 🗺️ Internet | IP addressing and routing |
| 🔗 Network Access (Link) | Physical transmission and framing |
 
---

#### 1. Application Layer
 
<details>
<summary><b>📖 Click to expand details</b></summary>

Combines the functions of:
- OSI Application Layer
- OSI Presentation Layer
- OSI Session Layer

**Protocols**
- HTTP
- HTTPS
- FTP
- SMTP
- DNS
</details>

---

### 2. Transport Layer
 
<details>
<summary><b>📖 Click to expand details</b></summary>
Provides communication between processes.
 
**Protocols**
- TCP
- UDP
**Functions**
- Segmentation
- Error control
- Reliability
- Port addressing
</details>

---

### 3. Internet Layer
 
<details>
<summary><b>📖 Click to expand details</b></summary>
Equivalent to the OSI Network Layer.
 
**Functions**
- IP Addressing
- Routing
- Packet forwarding
**Protocols**
- IPv4
- IPv6
**PDU:** `Packet`
 
</details>
---

### 4. Network Access (Link) Layer
 
<details>
<summary><b>📖 Click to expand details</b></summary>
Combines:
- OSI Data Link Layer
- OSI Physical Layer
**Functions**
- Framing
- MAC Addressing
- Physical transmission
**Technologies**
- Ethernet
- Wi-Fi
</details>
---
 
<a id="osi-vs-tcpip"></a>
## ⚖️ OSI vs TCP/IP
 
| Feature | OSI Model | TCP/IP Model |
|:---|:---|:---|
| **Number of Layers** | 7 | 4 |
| **Purpose** | Conceptual Model | Practical Model |
| **Internet Usage** | Rarely implemented directly | Used by the Internet |
| **Application Layer** | Separate | Combines Layers 5, 6, and 7 |
| **Lower Layers** | Separate Data Link & Physical | Combined into Link Layer |
 
---

<a id="example-sending-an-email"></a>
## ✉️ Example: Sending an Email
 
```text
1. Application Layer   → creates the email.
2. Presentation Layer  → encrypts and formats the data.
3. Session Layer       → manages the communication session.
4. Transport Layer     → (TCP) divides data into segments and adds port numbers.
5. Network Layer       → (IP) adds source and destination IP addresses.
6. Data Link Layer     → creates frames and adds MAC addresses.
7. Physical Layer      → sends bits through the network medium.
```
 
> At the receiver side, the process happens in **reverse order** until the email reaches the destination application.
 
---

<a id="exam-tips"></a>
## 🎯 Exam Tips
 
### OSI Layer Order (Top → Bottom)
 
```text
Application → Presentation → Session → Transport → Network → Data Link → Physical
```
 
> 💡 **Mnemonic:** *All People Seem To Need Data Processing*
 
### Important PDU Names
 
| Layer | PDU |
|:---|:---:|
| Application, Presentation, Session | Data |
| Transport | Segment |
| Network | Packet |
| Data Link | Frame |
| Physical | Bits |
 
### ✅ Remember
 
- **OSI Model** = 7 Layers = Theory/Conceptual
- **TCP/IP Model** = 4 Layers = Real Internet
- **TCP** = Reliable
- **UDP** = Faster but Less Reliable
- **IP** = Addressing & Routing
- **MAC Address** = Data Link Layer
- **Physical Layer** = Cables, Signals, Bits
---