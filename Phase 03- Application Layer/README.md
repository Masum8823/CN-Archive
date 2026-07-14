# 🌐 Application Layer — Complete Exam Notes

A simple, easy-to-read, exam-focused guide to the **Application Layer** protocols — the protocols that let apps, browsers, and network devices actually *talk* to each other. No boring textbook language here — just clear explanations, real-life examples, and everything you need before the exam.

![Layer](https://img.shields.io/badge/OSI%20Layer-Application-blue)
![Focus](https://img.shields.io/badge/Focus-Exam%20Ready-success)
![Language](https://img.shields.io/badge/Language-Easy%20English-orange)

---

## 📚 Table of Contents

- [🌐 Application Layer — Complete Exam Notes](#application-layer-complete-exam-notes)
  - [1. Introduction](#1-introduction)
  - [2. Management Protocols](#2-management-protocols)
    - [2.1 DNS – Domain Name System](#21-dns-domain-name-system)
    - [2.2 DHCP – Dynamic Host Configuration Protocol](#22-dhcp-dynamic-host-configuration-protocol)
    - [2.3 NTP – Network Time Protocol](#23-ntp-network-time-protocol)
    - [2.4 SNMP – Simple Network Management Protocol](#24-snmp-simple-network-management-protocol)
  - [3. Remote Communication Protocols](#3-remote-communication-protocols)
    - [3.1 Telnet](#31-telnet)
    - [3.2 SSH – Secure Shell](#32-ssh-secure-shell)
    - [3.3 RDP – Remote Desktop Protocol](#33-rdp-remote-desktop-protocol)
  - [4. File Transfer Protocols](#4-file-transfer-protocols)
    - [4.1 FTP – File Transfer Protocol](#41-ftp-file-transfer-protocol)
    - [4.2 SFTP – Secure File Transfer Protocol](#42-sftp-secure-file-transfer-protocol)
    - [4.3 TFTP – Trivial File Transfer Protocol](#43-tftp-trivial-file-transfer-protocol)
  - [5. Email Protocols](#5-email-protocols)
    - [5.1 SMTP – Simple Mail Transfer Protocol](#51-smtp-simple-mail-transfer-protocol)
    - [5.2 POP3 – Post Office Protocol v3](#52-pop3-post-office-protocol-v3)
    - [5.3 IMAP – Internet Message Access Protocol](#53-imap-internet-message-access-protocol)
  - [6. Web Browser Protocols](#6-web-browser-protocols)
    - [6.1 HTTP](#61-http)
    - [6.2 HTTPS](#62-https)
  - [7. Complete Course Quick Revision](#7-complete-course-quick-revision)
  - [8. Most Important Port Numbers](#8-most-important-port-numbers)
  - [9. Most Important Comparisons](#9-most-important-comparisons)
  - [10. Frequently Asked Exam Questions](#10-frequently-asked-exam-questions)
  - [11. Common Mistakes](#11-common-mistakes)
  - [12. Memory Tricks (All Protocols)](#12-memory-tricks-all-protocols)
  - [13. Last Minute Revision Sheet](#13-last-minute-revision-sheet)
  - [14. Final Exam Tips](#14-final-exam-tips)

---

<a id="1-introduction"></a>

## 1. Introduction

The **Application Layer** is the top layer of the network model — it's the layer closest to *you*, the user. Every time you open a browser, send an email, or connect to a remote server, an Application Layer protocol is working behind the scenes.

This chapter covers protocols in 5 groups:

| Group | Protocols |
|---|---|
| 🛠️ Management | DNS, DHCP, NTP, SNMP |
| 🖥️ Remote Communication | Telnet, SSH, RDP |
| 📁 File Transfer | FTP, SFTP, TFTP |
| 📧 Email | SMTP, POP3, IMAP |
| 🌍 Web Browsing | HTTP, HTTPS |

> 💡 **Exam Tip:** Almost every protocol here has a fixed **Port Number** and a **Transport Layer Protocol (TCP/UDP)**. These two things get asked A LOT in MCQ and Viva — memorize them first.

---

<a id="2-management-protocols"></a>

## 2. Management Protocols

These protocols help manage and organize how devices and networks operate — like resolving names, assigning addresses, syncing time, and monitoring devices.

---

<a id="21-dns-domain-name-system"></a>

### 2.1 DNS – Domain Name System

#### Definition
DNS is a protocol that turns a **domain name** (like `google.com`) into its actual **IP address** (like `142.250.194.78`), so your computer knows where to send the request.

#### Why Important?
Computers don't understand names like "google.com" — they only understand IP addresses. DNS is the bridge between human-friendly names and machine-friendly numbers.

#### Easy Explanation
Think of DNS like a **Phone Contact List** on your mobile. You don't remember everyone's phone number — you just save their name, and your phone looks up the number for you. DNS does exactly that for websites: you type a name, DNS finds the number (IP address).

#### Key Points
- Converts domain name → IP address
- Works behind the scenes every time you visit a website
- Detailed topics (Hierarchy, Record Types, Name Resolution) are covered separately in the DNS Network Services section

#### Remember
- `google.com` → `142.250.194.78` (name → number)

#### Diagram
```
User types: google.com
        │
        ▼
   [ DNS Server ]
        │
        ▼
 Returns IP: 142.250.194.78
        │
        ▼
 Browser connects using IP
```

#### Memory Trick
**DNS = "Digital Name Sorter"** — sorts names into numbers.

#### Exam Focus
- MCQ: "DNS converts domain name to ___" → IP Address
- Viva: Be ready to explain with the phonebook analogy
- Remember DNS itself doesn't have a fixed port shown here — it's expanded in a separate section

---

<a id="22-dhcp-dynamic-host-configuration-protocol"></a>

### 2.2 DHCP – Dynamic Host Configuration Protocol

| Port | Transport Layer Protocol |
|---|---|
| 67 (Server), 68 (Client) | UDP |

#### Definition
DHCP automatically assigns important network settings to a device when it joins a network — no manual setup needed.

#### Why Important?
Without DHCP, every device joining a network would need someone to **manually** type in an IP address, subnet mask, gateway, and DNS server. DHCP does all this automatically.

#### Easy Explanation
Imagine you check into a hotel. Instead of you choosing your own room number, the **reception desk automatically assigns you a room**. DHCP works the same way — it automatically "assigns a room" (IP address) to your device the moment it connects.

#### Key Points
DHCP automatically assigns:
- IP Address
- Subnet Mask
- Default Gateway
- DNS Server

#### Remember
- Uses **two UDP ports**: 67 (Server side) and 68 (Client side)
- Detailed working is discussed in the "Assigning IP Addresses" section

#### Example
Your phone connects to WiFi and instantly gets internet access without you typing any IP address — that's DHCP working in the background.

#### Diagram
```
[ New Device ]  --- "I need an IP!" --->  [ DHCP Server ]
[ New Device ]  <--- IP + Subnet + Gateway + DNS ---  [ DHCP Server ]
```

#### Memory Trick
**DHCP = "Digital Hotel Check-in Process"** — auto-assigns your room (IP) at check-in.

#### Exam Focus
- MCQ: DHCP uses which ports? → 67 and 68 (UDP)
- Viva: Explain the 4 things DHCP assigns
- Common confusion: DHCP is **UDP**, not TCP

---

<a id="23-ntp-network-time-protocol"></a>

### 2.3 NTP – Network Time Protocol

| Port | Transport Layer Protocol |
|---|---|
| 123 | TCP |

#### Definition
NTP automatically synchronizes a computer's clock/time with a network time server, so all devices agree on the exact same time.

#### Why Important?
Many network services (especially authentication/login systems) fail if the time on a device is wrong. Correct time = smooth network operation.

#### Easy Explanation
Think of NTP like a **wall clock in a school** — every classroom clock is synced to the main office clock so that all classes start and end at the same time. NTP keeps every device's "clock" in sync across the whole network.

#### Key Points
- Keeps system time accurate automatically
- Important for time-sensitive apps and protocols
- Wrong time on a device can block access to network services
- Authentication often fails if time isn't synced properly between devices

#### Remember
- Uses **TCP port 123**

#### Example
Windows "Date & Time" settings have an option "Set time automatically" using a time server like `time.windows.com` — that's NTP at work.

#### Diagram
```
[ Time Server ] --- Correct Time ---> [ Your PC's Clock ]
```

#### Memory Trick
**NTP = "Never (be) Time-off Protocol"** — keeps time always correct.

#### Exam Focus
- MCQ: NTP port → 123 (TCP)
- Viva: Why does wrong time break authentication?
- Remember: Time mismatch = login/authentication failure risk

---
<a id="24-snmp-simple-network-management-protocol"></a>

### 2.4 SNMP – Simple Network Management Protocol

| Port | Transport Layer Protocol |
|---|---|
| 161 | TCP |

#### Definition
SNMP is used to **monitor and manage** network devices — checking their health, status, and performance from a central point.

#### Why Important?
Network admins need to know if a device is overloaded, running low on memory, or facing high traffic — SNMP gives them that visibility without physically checking each device.

#### Easy Explanation
Think of SNMP like a **fitness tracker watch**. It doesn't control your body, but it constantly reports your heart rate, steps, and stats to an app. SNMP does the same for network devices — it reports memory, CPU, and bandwidth usage to the admin's monitoring tool.

#### Key Points
- Lets admins **monitor and manage** devices and traffic
- Devices report their state: Memory, CPU, Bandwidth
- Example tool: **PRTG Network Monitoring**

#### Remember
- Uses **TCP port 161**

#### Diagram
```
[ Router/Switch ] --- Memory, CPU, Bandwidth data ---> [ SNMP Monitoring Tool ]
```

#### Memory Trick
**SNMP = "System's Nerve Monitoring Protocol"** — like a nerve system reporting device health.

#### Exam Focus
- MCQ: SNMP port → 161 (TCP)
- Viva: Give an example SNMP tool (PRTG)
- Remember: SNMP monitors, doesn't just connect — think "network health checkup"

### 📝 Quick Revision — Management Protocols
- **DNS** → Name to IP (no fixed port covered here, detailed later)
- **DHCP** → Auto IP config, UDP 67/68
- **NTP** → Time sync, TCP 123
- **SNMP** → Device monitoring, TCP 161

---

<a id="3-remote-communication-protocols"></a>

## 3. Remote Communication Protocols

These protocols let you connect to and control another computer or device remotely — as if you were sitting right in front of it.

---

<a id="31-telnet"></a>

### 3.1 Telnet

| Port | Transport Layer Protocol |
|---|---|
| 23 | TCP |

#### Definition
Telnet is an old (legacy) protocol used to connect to a remote host — but it sends all data **without encryption**, in plain/clear text.

#### Why Important?
It's largely outdated now, but still important to know because it's a classic example of an **insecure** protocol — a favorite exam comparison topic against SSH.

#### Easy Explanation
Imagine sending a **postcard** instead of a sealed letter — anyone who touches it along the way can read every word. That's Telnet: your username, password, and commands travel in plain text, so anyone snooping on the network can see them.

#### Key Points
- Legacy protocol, considered insecure
- Data transferred in **clear text**
- Largely replaced by SSH
- Today mainly used to access managed network devices (like routers) via serial connection

#### Remember
- Uses **TCP port 23**

#### Diagram
```
[ Your PC ] ---(plain text data)---> [ Remote Host ]
      ⚠️ Anyone snooping can read this!
```

#### Memory Trick
**Telnet = "Tell-Net"** — it literally "tells" your data to the whole network in plain text (insecure).

#### Exam Focus
- MCQ: Telnet port → 23 (TCP)
- Viva: Why is Telnet insecure?
- Common comparison: Telnet vs SSH (see comparison table below)

---

<a id="32-ssh-secure-shell"></a>

### 3.2 SSH – Secure Shell

| Port | Transport Layer Protocol |
|---|---|
| 22 | TCP |

#### Definition
SSH is a cryptographic (encrypted) protocol used to securely connect to and control a remote host through a terminal console.

#### Why Important?
SSH is the **secure replacement** for Telnet — it's the standard way admins connect to servers and network devices today.

#### Easy Explanation
If Telnet is like sending a postcard, SSH is like sending a **locked, sealed envelope** that only the receiver has the key to open. SSH encrypts everything using Public Key Infrastructure (PKI), so even if someone intercepts the data, they can't read it.

#### Key Points
- Cryptographic (encrypted) protocol
- Uses a terminal console
- Common on Unix/Linux, but also available on Windows and Mac OS
- Encrypts data using **Public Key Infrastructure (PKI)**
- Secure replacement for Telnet

#### Remember
- Uses **TCP port 22**

#### Diagram
```
[ Your PC ] ---(🔒 encrypted data)---> [ Remote Host ]
      ✅ Safe even if intercepted
```

#### Memory Trick
**SSH = "Safely Shielded Host access"** — locked and safe.

#### Exam Focus
- MCQ: SSH port → 22 (TCP)
- Viva: What makes SSH secure? (PKI encryption)
- Very common comparison question: Telnet vs SSH

---

<a id="33-rdp-remote-desktop-protocol"></a>

### 3.3 RDP – Remote Desktop Protocol

| Port | Transport Layer Protocol |
|---|---|
| 3389 | TCP |

#### Definition
RDP is a Microsoft protocol that lets you remotely connect to, view, and fully control another Windows computer's desktop.

#### Why Important?
It's the built-in way Windows machines allow remote access — commonly used by IT support and remote workers.

#### Easy Explanation
Imagine controlling a TV with a **remote control** — you're not physically touching the TV, but you can change channels, volume, etc. from anywhere in the room. RDP works similarly — you control someone's Windows desktop screen from your own PC.

#### Key Points
- Microsoft protocol
- Lets you view and control a remote Windows desktop
- Built directly into the Windows operating system

#### Remember
- Uses **TCP port 3389**

#### Diagram
```
[ Your PC ] ---(view & control)---> [ Remote Windows Desktop ]
```

#### Memory Trick
**RDP = "Remote Desktop = Port 3-3-8-9"** — just link the "3389" digits to "RDP" since it's a Microsoft-only feature.

#### Exam Focus
- MCQ: RDP port → 3389 (TCP)
- Viva: Is RDP available on Linux? (No, it's built for Microsoft OS, though clients exist for other OS)

### 📝 Quick Revision — Remote Communication Protocols
- **Telnet** → Insecure, plain text, TCP 23
- **SSH** → Secure, encrypted, TCP 22
- **RDP** → Microsoft desktop remote control, TCP 3389

---

<a id="4-file-transfer-protocols"></a>

## 4. File Transfer Protocols

These protocols are used to move files between computers/servers.

---

<a id="41-ftp-file-transfer-protocol"></a>

### 4.1 FTP – File Transfer Protocol

| Ports | Transport Layer Protocol |
|---|---|
| 20 (Data), 21 (Control) | TCP |

#### Definition
FTP is a legacy protocol used to transfer files between systems — supporting full file operations like viewing, listing, adding, and deleting files.

#### Why Important?
It's one of the oldest and most well-known file transfer methods, and it's a common exam topic because of its two-port system and its insecurity.

#### Easy Explanation
Think of FTP like an **old delivery service** that doesn't seal packages — anyone along the delivery route can open and see what's inside. FTP sends data in **clear text**, so it's insecure, similar to Telnet.

#### Key Points
- Legacy protocol, being replaced by SFTP
- Can authenticate with username/password OR allow anonymous login
- Data sent in **clear text** (insecure)
- Full-featured: view, list, add, delete files and folders
- Uses **two TCP ports**:
  - **Port 20** → Data transfer
  - **Port 21** → Control (commands)

#### Remember
- Two ports: 20 for Data, 21 for Control

#### Diagram
```
[ Client ] ---Port 21 (Commands)---> [ FTP Server ]
[ Client ] ---Port 20 (File Data)---> [ FTP Server ]
```

#### Memory Trick
**FTP = "20 for File, 21 for Formal command"**

#### Exam Focus
- MCQ: FTP uses which 2 ports? → 20 and 21
- Viva: Which port is for data, which is for control?
- Common confusion: FTP is insecure (clear text) — don't mix up with SFTP

---

<a id="42-sftp-secure-file-transfer-protocol"></a>

### 4.2 SFTP – Secure File Transfer Protocol

| Port | Transport Layer Protocol |
|---|---|
| 22 | TCP |

#### Definition
SFTP is the secure, encrypted version of FTP — it uses SSH to protect the file transfer.

#### Why Important?
It solves FTP's biggest weakness (no encryption) by riding on top of SSH's secure tunnel.

#### Easy Explanation
If FTP is an open delivery box, SFTP is the same delivery but now inside a **locked security van** (SSH) — nobody can peek inside during transit.

#### Key Points
- Secure cryptographic version of FTP
- Provides file transfer **over SSH**
- Uses the **same port as SSH**

#### Remember
- Uses **TCP port 22** — exactly the same as SSH

#### Diagram
```
[ Client ] ---(🔒 encrypted file transfer via SSH)---> [ SFTP Server ]
```

#### Memory Trick
**SFTP = "Secure FTP shares SSH's home"** (same port 22).

#### Exam Focus
- MCQ: SFTP port → 22 (TCP) — same as SSH!
- Viva: Why does SFTP use SSH's port? (Because it transfers files through the SSH secure tunnel)

---

<a id="43-tftp-trivial-file-transfer-protocol"></a>

### 4.3 TFTP – Trivial File Transfer Protocol

| Port | Transport Layer Protocol |
|---|---|
| 69 | UDP |

#### Definition
TFTP is a very basic, "bare-bones" version of FTP used only for simple file downloads — with no authentication and no folder browsing.

#### Why Important?
It's commonly used in real networking work to push software/firmware updates to routers and switches.

#### Easy Explanation
Think of TFTP like a **vending machine** — you must know the exact item number (exact file and location) to get something. There's no browsing around like a store (no directory navigation), and no ID check (no authentication).

#### Key Points
- Bare-bones version of FTP
- **No authentication** support
- **No directory navigation** — must request the exact file and location
- Often used to transfer router/switch software images during upgrades

#### Remember
- Uses **UDP port 69**

#### Diagram
```
[ Client: "Give me exact file X" ] ---> [ TFTP Server ] ---> [ Sends file directly ]
```

#### Memory Trick
**TFTP = "Tiny File Transfer, Please"** — small and simple, UDP 69.

#### Exam Focus
- MCQ: TFTP port → 69 (UDP)
- Viva: How is TFTP different from FTP? (No authentication, no navigation, UDP not TCP)
- Common trick question: TFTP is the ONLY file transfer protocol here using **UDP**

### 📝 Quick Revision — File Transfer Protocols
- **FTP** → Insecure, 2 ports (20 Data, 21 Control), TCP
- **SFTP** → Secure (via SSH), port 22, TCP
- **TFTP** → Basic, no auth, no navigation, UDP port 69

---

## 5. Email Protocols

These protocols handle sending and receiving emails.

---

<a id="51-smtp-simple-mail-transfer-protocol"></a>

### 5.1 SMTP – Simple Mail Transfer Protocol

| Port | Transport Layer Protocol |
|---|---|
| 25 | TCP |

#### Definition
SMTP is used to **send/deliver** emails from an email client (like Outlook) to a destination email server.

#### Why Important?
Every email you send goes through SMTP first — it's the "sending" half of the email system.

#### Easy Explanation
Think of SMTP like the **postman who picks up your letter** and delivers it to the correct post office. It only handles sending — not reading or storing your inbox.

#### Key Points
- Delivers emails from client → destination email server
- Can use encryption (recommended) or plain text

#### Remember
- Uses **TCP port 25**
- SMTP = **Sending** emails only

#### Diagram
```
[ Email Client (Outlook) ] ---SMTP (send)---> [ Destination Mail Server ]
```

#### Memory Trick
**SMTP = "Sending Mail To People"**

#### Exam Focus
- MCQ: SMTP port → 25 (TCP)
- Viva: Is SMTP for sending or receiving? → Sending only

---

<a id="52-pop3-post-office-protocol-v3"></a>

### 5.2 POP3 – Post Office Protocol v3

| Port | Transport Layer Protocol |
|---|---|
| 110 | TCP |

#### Definition
POP3 is used to **retrieve/download** emails from an email server to your device.

#### Why Important?
It's one of the two major protocols (along with IMAP) for reading your received emails — a very common exam comparison topic.

#### Easy Explanation
Think of POP3 like **collecting your letters from the post office and taking them all home** — once collected, they're usually removed from the post office and now live only on your device.

#### Key Points
- Retrieves emails from a mail server
- Can use encryption (recommended) or plain text

#### Remember
- Uses **TCP port 110**

#### Diagram
```
[ Mail Server ] ---POP3 (download & often remove)---> [ Client Device ]
```

#### Memory Trick
**POP3 = "Pick uP & Own"** — you pick it up and it becomes yours (downloaded locally).

#### Exam Focus
- MCQ: POP3 port → 110 (TCP)
- Viva: Difference between POP3 and IMAP? (see comparison table)

---

<a id="53-imap-internet-message-access-protocol"></a>

### 5.3 IMAP – Internet Message Access Protocol

| Port | Transport Layer Protocol |
|---|---|
| 143 | TCP |

#### Definition
IMAP is another email protocol (replacing POP3) that lets users access email directly on the server — either reading it there or downloading it, while keeping it synced across devices.

#### Why Important?
Modern email use (checking mail on phone, laptop, tablet all at once) depends on IMAP — this is why services like Gmail use it.

#### Easy Explanation
Think of IMAP like reading your mail **directly at the post office through a window**, without taking it home — so no matter which "window" (device) you check from, you see the same mail, same status (read/unread).

#### Key Points
- Quickly replacing POP3
- Lets users read on server OR download to device
- Popular for multi-device access (phone + laptop + tablet)
- Web-based clients like **Gmail** use IMAP

#### Remember
- Uses **TCP port 143**

#### Diagram
```
[ Mail Server ] <--- synced access ---> [ Phone, Laptop, Tablet ]
```

#### Memory Trick
**IMAP = "I Manage All Places"** — same inbox synced everywhere.

#### Exam Focus
- MCQ: IMAP port → 143 (TCP)
- Viva: Why is IMAP better for multi-device use than POP3?

### 📝 Quick Revision — Email Protocols
- **SMTP** → Sending emails, TCP 25
- **POP3** → Downloading emails (usually removes from server), TCP 110
- **IMAP** → Syncs emails across devices, TCP 143

---

<a id="6-web-browser-protocols"></a>

## 6. Web Browser Protocols

These protocols power your everyday web browsing.

---

<a id="61-http"></a>

### 6.1 HTTP – Hypertext Transfer Protocol

| Port | Transport Layer Protocol |
|---|---|
| 80 | TCP |

#### Definition
HTTP provides browsing services for the World Wide Web — it retrieves web page content from a web server and delivers it to your browser.

#### Why Important?
It's the foundation protocol of the entire web — every website request without "S" (secure) uses this.

#### Easy Explanation
Think of HTTP like ordering food **without a sealed delivery bag** — the delivery guy (and anyone nearby) could see exactly what you ordered. Requests and pages are sent in **plain text**, which means anyone snooping can read them.

#### Key Points
- Retrieves web page content from a web server
- Requests/responses are made in **HTML** format
- Data is sent in **plain text**

#### Remember
- Uses **TCP port 80**

#### Diagram
```
[ Browser ] ---HTTP request---> [ Web Server ]
[ Browser ] <---HTML page (plain text)--- [ Web Server ]
```

#### Memory Trick
**HTTP = "Handled Text Transfer, Plainly"** — plain text, no lock.

#### Exam Focus
- MCQ: HTTP port → 80 (TCP)
- Viva: Why is HTTP considered insecure?

---

<a id="62-https"></a>

### 6.2 HTTPS – HTTP Secure

| Port | Transport Layer Protocol |
|---|---|
| 443 | TCP |

#### Definition
HTTPS is the secure version of HTTP — it uses SSL/TLS encryption to protect the data being exchanged between your browser and the website.

#### Why Important?
It's the standard today for any website handling sensitive data (logins, payments, personal info) — recognized by the padlock icon in your browser.

#### Easy Explanation
If HTTP is an unsealed package, HTTPS is the same package now inside a **tamper-proof sealed box** — using SSL/TLS encryption and Public Key Infrastructure (PKI) so no one in between can read or alter your data.

#### Key Points
- HTTP over **SSL (Secure Socket Layer)** or **TLS (Transport Layer Security)**
- Encrypts HTTP content
- Utilizes **Public Key Infrastructure (PKI)**

#### Remember
- Uses **TCP port 443**

#### Diagram
```
[ Browser ] ---(🔒 encrypted HTTPS)---> [ Web Server ]
```

#### Memory Trick
**HTTPS = "HTTP That's Properly Secured"**

#### Exam Focus
- MCQ: HTTPS port → 443 (TCP)
- Viva: What does HTTPS use for security? (SSL/TLS + PKI)
- Very common comparison: HTTP vs HTTPS

### 📝 Quick Revision — Web Browser Protocols
- **HTTP** → Plain text browsing, TCP 80
- **HTTPS** → Encrypted browsing (SSL/TLS + PKI), TCP 443

---

<a id="7-complete-course-quick-revision"></a>

## 7. Complete Course Quick Revision

- **DNS** → Name → IP address resolution (like a phonebook)
- **DHCP** → Auto-assigns IP, Subnet, Gateway, DNS (UDP 67/68)
- **NTP** → Syncs device time (TCP 123)
- **SNMP** → Monitors device health: CPU, memory, bandwidth (TCP 161)
- **Telnet** → Insecure remote access, plain text (TCP 23)
- **SSH** → Secure remote access, encrypted with PKI (TCP 22)
- **RDP** → Microsoft remote desktop control (TCP 3389)
- **FTP** → File transfer, insecure, 2 ports: 20 Data / 21 Control (TCP)
- **SFTP** → Secure file transfer over SSH (TCP 22)
- **TFTP** → Basic file transfer, no auth/navigation (UDP 69)
- **SMTP** → Sends email (TCP 25)
- **POP3** → Downloads email, usually removes from server (TCP 110)
- **IMAP** → Syncs email across devices (TCP 143)
- **HTTP** → Plain text web browsing (TCP 80)
- **HTTPS** → Encrypted web browsing with SSL/TLS (TCP 443)

---
