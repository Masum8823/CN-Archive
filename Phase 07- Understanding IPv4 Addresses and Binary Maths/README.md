# 🌐 Understanding IPv4 Addresses & Binary Math — Complete Exam Notes

![Course](https://img.shields.io/badge/Course-Data%20Communications%20(CSE%203227)-blue)
![Topic](https://img.shields.io/badge/Chapter-IPv4%20%26%20Binary%20Math-green)
![Level](https://img.shields.io/badge/Level-Exam%20Ready-orange)
![Made%20with](https://img.shields.io/badge/Made%20with-%E2%9D%A4%EF%B8%8F%20Easy%20English-red)

> This README covers everything about **IPv4 addresses, binary math, IP classes, subnet masks, CIDR notation, public/private IPs, and the loopback address**. Read this once before exam and you're fully covered.

---

## 📑 Table of Contents

* [1. What is an IP Address?](#1-what-is-ip)
* [2. IPv4 Address Anatomy](#2-ipv4-anatomy)
* [3. Network Portion vs Host Portion](#3-network-host)
* [4. IPv4 Address Components (IP, Subnet Mask, Gateway)](#4-ipv4-components)
* [5. Binary Math Basics — Binary to Decimal](#5-binary-to-decimal)
* [6. Binary Math Basics — Decimal to Binary](#6-decimal-to-binary)
* [7. IP Address Conversion Process](#7-ip-conversion-process)
* [8. IPv4 Address Classes (Simplified)](#8-classes-simplified)
* [9. IPv4 Address Classes (Detailed)](#9-classes-detailed)
* [10. Default Subnet Masks](#10-default-subnet-masks)
* [11. Practice — Identify the Class](#11-practice-class)
* [12. CIDR Notation](#12-cidr)
* [13. The Power of 2](#13-power-of-2)
* [14. Calculating Hosts Per Network](#14-hosts-per-network)
* [15. Public vs Private IP Addresses](#15-public-vs-private)
* [16. Private IP Address Ranges](#16-private-ranges)
* [17. The Loopback Address](#17-loopback)
* [18. Quick Revision (Whole Chapter)](#18-quick-revision)
* [19. Frequently Asked Exam Questions](#19-faq)
* [20. Common Mistakes](#20-common-mistakes)
* [21. Memory Tricks](#21-memory-tricks)
* [22. Exam Tips](#22-exam-tips)

---

<a id="1-what-is-ip"></a>

## 1. What is an IP Address?

### Definition
An **IP Address** is a **logical address** used to uniquely identify a device on an IP network. It works at the **Network Layer** of the OSI model.

### Why Important?
Without an IP address, no device could be found or reached on a network — it's literally the "home address" of every device on the internet.

### Easy Explanation
Think of an IP address like your home's postal address — it tells the network exactly where to deliver data, just like a postman needs your address to deliver a letter.

### Key Points
- IP Address = **logical address** (not physical, can change)
- Works at the **Network Layer**
- Two versions exist:
  - **IPv4** (this chapter)
  - **IPv6** (covered later in the course)

### Exam Focus
- Which OSI layer does IP address belong to? → **Network Layer**
- IPv4 vs IPv6 — just know these are two versions, IPv6 covered separately

---

<a id="2-ipv4-anatomy"></a>

## 2. IPv4 Address Anatomy

### Definition
An IPv4 address is made up of **32 binary bits**, divided into **4 octets** (1 octet = 8 bits). Each octet is converted into decimal and separated by dots — this is why it's called **dotted decimal format**.

### Easy Explanation
Think of an IP address like a 4-part code, where each part is a number between 0-255, separated by dots. Behind the scenes, computers see it all in binary (1s and 0s); we just convert it to decimal so it's easier for humans to read and remember.

### Example
```
Decimal:  192      .   168      .    1       .   131
Binary:   11000000 . 10101000  . 00000001   . 10000011
```

### Table View
| First Octet | Second Octet | Third Octet | Fourth Octet |
|---|---|---|---|
| 192 | 168 | 1 | 131 |
| 11000000 | 10101000 | 00000001 | 10000011 |
| 8 bits | 8 bits | 8 bits | 8 bits |

### Key Points
- 8 bits = 1 byte = 1 octet
- 32 bits = 4 bytes = 4 octets
- Format: **dotted decimal** (e.g., 192.168.1.131)

### Shortcut Memory Trick
**"8-8-8-8 = 32"** — each of the 4 octets is 8 bits, total 32 bits.

### Exam Focus
- Convert a given decimal IP to binary and vice versa (guaranteed numerical question)
- Know exact terms: octet, byte, dotted decimal format

---


<a id="9-classes-detailed"></a>

## 9. IPv4 Address Classes (Detailed)

### Full Table
| Class | Leading Bits | Network Bits | Host Bits | Number of Networks | Hosts Per Network | Default Subnet Mask |
|---|---|---|---|---|---|---|
| **A** | 0 (1–126) | 8 | 24 | 128 (2⁷) | 16,777,216 (2²⁴) | 255.0.0.0 |
| **B** | 10 (128–191) | 16 | 16 | 16,384 (2¹⁴) | 65,536 (2¹⁶) | 255.255.0.0 |
| **C** | 110 (192–223) | 24 | 8 | 2,097,152 (2²¹) | 256 (2⁸) | 255.255.255.0 |
| **D (multicast)** | 1110 (224–239) | Not Defined | Not Defined | Not Defined | Not Defined | Not Defined |
| **E (reserved)** | 1111 (240–255) | Not Defined | Not Defined | Not Defined | Not Defined | Not Defined |

### Easy Explanation
- **Leading bits** are like a "signature" at the very start of the first octet that tells you which class an IP belongs to just by looking at the first few bits
- **Class D** is reserved for **multicast** (one sender, many receivers — like streaming to a group)
- **Class E** is **reserved** for experimental/future use — you'll basically never see it used

### Key Points
- Class A starts with a leading bit **0**
- Class B starts with leading bits **10**
- Class C starts with leading bits **110**
- Class D starts with **1110** (multicast)
- Class E starts with **1111** (reserved)

### Exam Focus
- Memorize leading bits per class — **very common in MCQ**
- Know that D = multicast, E = reserved (not used for regular host addressing)

---


<a id="10-default-subnet-masks"></a>

## 10. Default Subnet Masks

### Definition
The **Subnet Mask** tells you which part of the IP address is the Network portion and which part is the Host portion. Each class has its own **default** subnet mask.

### Easy Explanation & Example

| Class | Example IP | Subnet Mask (Decimal) | Subnet Mask (Binary) |
|---|---|---|---|
| **A** | 10.0.0.15 | 255.0.0.0 | 11111111.00000000.00000000.00000000 |
| **B** | 172.16.0.110 | 255.255.0.0 | 11111111.11111111.00000000.00000000 |
| **C** | 192.168.1.50 | 255.255.255.0 | 11111111.11111111.11111111.00000000 |

### Key Points
- Wherever the subnet mask has **255 (all 1s)** → that octet is **Network**
- Wherever the subnet mask has **0 (all 0s)** → that octet is **Host**

### Shortcut Memory Trick
**"255 = Network, 0 = Host"** — just look at the subnet mask pattern to instantly know the class.

### Exam Focus
- Given an IP + subnet mask, identify which octets are network vs host
- Memorize default subnet masks for A, B, C exactly

---

<a id="11-practice-class"></a>

## 11. Practice — Identify the Class

### Practice Questions (from the slides)

| IP Address | Subnet Mask | Class |
|---|---|---|
| 9.10.40.15 | 255.0.0.0 | **A** (first octet 1-126, mask 255.0.0.0) |
| 135.240.110.100 | 255.255.0.0 | **B** (first octet 128-191, mask 255.255.0.0) |
| 196.200.10.5 | 255.255.255.0 | **C** (first octet 192-223, mask 255.255.255.0) |

### Easy Explanation
The fastest way to identify a class: **just look at the first octet number** and match it against the ranges in Section 8/9. The subnet mask is a second confirmation.

### Exam Focus
- This exact style of question ("what class is this IP?") is **very likely** to appear — practice recognizing ranges instantly

---

<a id="12-cidr"></a>

## 12. CIDR Notation

### Definition
**CIDR (Classless Inter-Domain Routing)** is a method of subnetting that uses **"slash" notation** to show how many bits belong to the Subnet Mask — instead of writing the full dotted-decimal mask.

### Easy Explanation
Instead of writing `255.255.255.0`, you can just write `/24` — meaning "24 bits are set to 1 in the subnet mask." It's a shortcut.

### Examples
| CIDR | Equivalent Subnet Mask |
|---|---|
| /8 | 255.0.0.0 |
| /16 | 255.255.0.0 |
| /24 | 255.255.255.0 |
| /25 | 255.255.255.128 |

### More Examples
- `192.168.1.0 /24` = `255.255.255.0`
- `10.1.0.0 /16` = `255.255.0.0`
- `196.10.10.0 /25` = `255.255.255.128`

### Shortcut Memory Trick
**"/number = how many 1s from the left"** — `/8` means the first 8 bits are 1 (11111111.00000000.00000000.00000000).

### Exam Focus
- Convert CIDR (/24, /16, /8, /25) to dotted-decimal subnet mask and vice versa — **guaranteed question type**

---

<a id="13-power-of-2"></a>

## 13. The Power of 2

### Why Important?
Subnetting math is **built entirely on powers of 2** — you cannot calculate number of networks/hosts without memorizing this table.

### Table (Memorize This!)
| Power | Value | Power | Value |
|---|---|---|---|
| 2¹ | 2 | 2⁷ | 128 |
| 2² | 4 | 2⁸ | 256 |
| 2³ | 8 | 2⁹ | 512 |
| 2⁴ | 16 | 2¹⁰ | 1,024 |
| 2⁵ | 32 | 2¹¹ | 2,048 |
| 2⁶ | 64 | 2¹² | 4,096 |

### Shortcut Memory Trick
Just remember: **double the previous number each time** → 2, 4, 8, 16, 32, 64, 128, 256, 512, 1024, 2048, 4096...

### Exam Focus
- Memorize at least up to 2¹² — subnetting problems depend on quick recall of these values

---


<a id="14-hosts-per-network"></a>

## 14. Calculating Hosts Per Network

### Definition
The formula to calculate how many usable host addresses exist in a network:
```
Hosts Per Network = 2^h − 2
```
where **h** = number of host bits available.

### Why subtract 2?
Because every network reserves **2 special addresses** that can't be assigned to a device:
1. **Network Address** (identifies the network itself, all host bits = 0)
2. **Broadcast Address** (used to send to everyone on that network, all host bits = 1)

### Example Table
| Class | Host Bits (h) | Formula | Result |
|---|---|---|---|
| **A** | 24 | 2²⁴ − 2 | 16,777,214 |
| **B** | 16 | 2¹⁶ − 2 | 65,534 |
| **C** | 8 | 2⁸ − 2 | 254 |

### Key Points
- Always subtract 2 from the raw power-of-2 result
- The 2 reserved addresses are: **Network Address** and **Broadcast Address**

### Exam Focus
- This formula (2^h − 2) is a **must-memorize** — appears in almost every subnetting numerical
- Be ready to explain *why* we subtract 2 (not just apply the formula blindly)

---


<a id="15-public-vs-private"></a>

## 15. Public vs Private IP Addresses

### Definition
- **Public IP Address**: "Registered," globally unique, assigned by an ISP, used to communicate over the internet.
- **Private IP Address**: "Unregistered," free for anyone to use inside their own internal network, not routable on the public internet directly.

### Easy Explanation
Think of a private IP like your **internal office extension number** (e.g., "Dial 105 for Accounts") — it only works inside your building. A public IP is like your **full mobile number** that anyone in the world can dial.

### Comparison Table
| Feature | Public IP | Private IP |
|---|---|---|
| Registration | Registered (via ISP) | Unregistered (free for anyone) |
| Uniqueness | Must be globally unique | Can be reused in different networks |
| Usage | Web servers, DNS servers, Routers | Internal home/office devices |
| Routable on Internet? | Yes | No (needs NAT) |
| Example | 140.100.100.150 | 192.168.1.10 |

### Why Private IPs Exist
By the **early 1990s**, the world started running out of public IP addresses. To solve this, **Private IP Addresses + NAT (Network Address Translation)** were introduced — letting multiple private devices share one public IP when accessing the internet.

### Easy Diagram
```
[Private Network: 192.168.100.x devices] --- Router (NAT) --- [Public IP: 140.100.100.150] --- Internet
```

### Key Points
- Private IPs use **NAT** to communicate with public networks
- Private IPs can be reused in millions of different homes/offices without conflict — because they never leave their own local network

### Exam Focus
- Explain why NAT was invented (running out of public IPs)
- Public vs Private comparison table — common short question

---

<a id="16-private-ranges"></a>

## 16. Private IP Address Ranges

### Definition (Memorize This Table!)
| Class | IP Address Range | Network ID(s) (CIDR) | Number of Addresses |
|---|---|---|---|
| **A** | 10.0.0.0 – 10.255.255.255 | 10.0.0.0 /8 (1 network) | 16,777,216 per Network ID |
| **B** | 172.16.0.0 – 172.31.255.255 | 172.16.0.0 – 172.31.0.0 /16 (16 networks) | 65,534 per Network ID |
| **C** | 192.168.0.0 – 192.168.255.255 | 192.168.0.0 – 192.168.255.0 /24 (256 networks) | 254 per Network ID |

### Shortcut Memory Trick
**"10, 172.16-31, 192.168"** — the 3 famous private ranges. Almost every home router uses **192.168.x.x**.

### Exam Focus
- Memorize these 3 private ranges exactly (very high chance of MCQ/short question)
- Know how many private networks exist per class (1 for A, 16 for B, 256 for C)

---

<a id="17-loopback"></a>

## 17. The Loopback Address

### Definition
The range **127.0.0.0 to 127.255.255.255** is reserved as the **loopback address** — meaning a host's own address, also called **localhost**.

### Why Important?
It's used to test whether **TCP/IP is correctly installed and working** on your own computer — without needing any actual network connection.

### Easy Explanation
Think of loopback like talking to yourself in a mirror — the data never actually leaves your computer. It goes out, and immediately "loops back" to itself, without ever touching the physical network card (NIC).

### Key Points
- Default loopback address = **127.0.0.1**
- Data sent to loopback is forwarded to a **virtual network interface** inside the OS — the real network card (NIC) is never involved
- If you can successfully ping the loopback, your TCP/IP stack is **working correctly**

### How to Test It
```
ping 127.0.0.1
ping localhost
ping loopback
```

### Exam Focus
- What is the default loopback address? → **127.0.0.1**
- What is loopback used for? → **Testing/diagnosing TCP/IP installation on your own machine**
- Understand that loopback traffic never touches the actual NIC (network card)

---

