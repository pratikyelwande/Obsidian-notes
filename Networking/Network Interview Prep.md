
### ==What is a Network? ==

> **Definition:**  
> A **network** is a group of two or more devices (like computers, servers, routers, switches) connected together to **share resources**, **exchange data**, and **communicate** with each other.
---

### 🔑 **Most Commonly Asked Network Ports**

|Port|Protocol|Service / Usage|
|---|---|---|
|**20**|TCP|FTP (File Transfer Protocol - Data)|
|**21**|TCP|FTP (Control)|
|**22**|TCP|SSH (Secure Shell - Remote Login)|
|**23**|TCP|Telnet (Unsecure Remote Login)|
|**25**|TCP|SMTP (Simple Mail Transfer Protocol)|
|**53**|UDP/TCP|DNS (Domain Name System)|
|**67**|UDP|DHCP (Server)|
|**68**|UDP|DHCP (Client)|
|**69**|UDP|TFTP (Trivial File Transfer Protocol)|
|**80**|TCP|HTTP (Web Browsing)|
|**110**|TCP|POP3 (Email Retrieval)|
|**123**|UDP|NTP (Network Time Protocol)|
|**143**|TCP|IMAP (Email Retrieval)|
|**161**|UDP|SNMP (Simple Network Management)|
|**443**|TCP|HTTPS (Secure Web Browsing)|
|**445**|TCP|SMB (Windows File Sharing)|
|**3389**|TCP|RDP (Remote Desktop Protocol)|

---

### 🎯 **Tips to Remember**

- **HTTP vs HTTPS**: 80 (HTTP) is insecure; 443 (HTTPS) is secure.
    
- **SSH (22)** and **RDP (3389)** are for remote access — secure vs GUI-based.
    
- **FTP (20/21)** vs **TFTP (69)**: FTP is secure and has control/data channels; TFTP is simple.
    
- **DNS (53)** can use both TCP and UDP.
    
- **DHCP**: 67 = server, 68 = client.

### 🧩 Types of Networks Explained:

---

### 1. **LAN (Local Area Network)**

- **Scope**: Small area — like a home, office, school, or building.
    
- **Speed**: High speed (typically Ethernet or Wi-Fi).
    
- **Example**:
    
    > All computers and printers in your office connected via a Wi-Fi router — that's a **LAN**.
    
- **Use Case**: File sharing, printer access, internal communication.

---
### 2. **WAN (Wide Area Network)**

- **Scope**: Very large geographical area — across cities, states, or countries.
    
- **Speed**: Slower than LAN (depends on ISP).
    
- **Example**:
    
    > The **Internet** is the best example of a WAN — it's a network of networks.
    
- **Use Case**: Connects multiple LANs remotely (e.g., corporate branch offices).
    

---

### 3. **MAN (Metropolitan Area Network)**

- **Scope**: Covers a **city or a large campus**.
    
- **Example**:
    
    > A university with multiple buildings in a city, all connected using fiber optics — that's a **MAN**.
    
- **Use Case**: Government offices, university campuses, or large organizations spread across a city.

### 🎯 Interview Example:

> **Q: What is a protocol? Can you name a few?**  
> **A:** A protocol is a set of rules that governs data communication over a network. Common protocols include HTTP, HTTPS, FTP, TCP, UDP, DNS, and SMTP.

## 📘 Number System Notes (with Examples & Conversions)

---
### 1. 🔢 **Types of Number Systems**

|System|Base|Digits Used|Example|
|---|---|---|---|
|Binary|2|0, 1|`1010`|
|Decimal|10|0–9|`345`|
|Octal|8|0–7|`17`|
|Hexadecimal|16|0–9, A–F (A=10…F=15)|`2F`|

---

### 2. 🔁 **Conversions with Examples**

---
#### ✅ Binary ➡ Decimal

📌 Binary: `1011`  
Step:  
= (1×2³) + (0×2²) + (1×2¹) + (1×2⁰)  
= 8 + 0 + 2 + 1 = **11**

---

#### ✅ Decimal ➡ Binary

📌 Decimal: `13`  
Step:  
Divide by 2 and write remainder:

|Division|Quotient|Remainder|
|---|---|---|
|13 ÷ 2|6|1|
|6 ÷ 2|3|0|
|3 ÷ 2|1|1|
|1 ÷ 2|0|1|

Read bottom to top → **1101**

---

#### ✅ Decimal ➡ Octal

📌 Decimal: `65`  
Step:

|Division|Quotient|Remainder|
|---|---|---|
|65 ÷ 8|8|1|
|8 ÷ 8|1|0|
|1 ÷ 8|0|1|

Read bottom to top → **101 (Octal)**

---

#### ✅ Octal ➡ Decimal

📌 Octal: `157`  
= (1×8²) + (5×8¹) + (7×8⁰)  
= 64 + 40 + 7 = **111**

---

#### ✅ Decimal ➡ Hexadecimal

📌 Decimal: `254`  
Step:

|Division|Quotient|Remainder|
|---|---|---|
|254 ÷ 16|15|14 (E)|
|15 ÷ 16|0|15 (F)|

Read bottom to top → **FE**

---

#### ✅ Hexadecimal ➡ Decimal

📌 Hex: `3A`  
= (3 × 16¹) + (10 × 16⁰)  
= 48 + 10 = **58**

---

#### ✅ Binary ➡ Octal

Group 3 bits from right → `110110` → `110` `110`  
Each group to decimal: `6` `6` → **66 (Octal)**

---

#### ✅ Binary ➡ Hexadecimal

Group 4 bits from right → `10111100` → `1011` `1100`  
→ `B` `C` → **BC**

---

#### ✅ Hexadecimal ➡ Binary

📌 Hex: `2F`  
2 → `0010`, F → `1111`  
→ **00101111**

---

#### ✅ Octal ➡ Binary

📌 Octal: `75`  
7 → `111`, 5 → `101`  
→ **111101**

---

### 📌 Summary Table (Quick Reference)

|From → To|Method|
|---|---|
|Binary → Decimal|Multiply each bit by 2ⁿ and add|
|Decimal → Binary|Divide by 2 and reverse remainders|
|Decimal → Octal|Divide by 8 and reverse remainders|
|Octal → Decimal|Multiply digits by 8ⁿ and add|
|Decimal → Hex|Divide by 16 and reverse remainders|
|Hex → Decimal|Multiply digits by 16ⁿ and add|
|Binary → Octal|Group 3 bits from right, convert to octal|
|Binary → Hex|Group 4 bits from right, convert to hex|
|Hex/Octal → Binary|Convert each digit to 4/3-bit binary|
## 🧠 ==OSI Model== (Open Systems Interconnection Model)

The OSI model is a **7-layer framework** that standardizes the functions of a telecommunication or computing system **without regard to its underlying internal structure**.

---

### ==🔁 7 Layers of OSI Model (Top to Bottom):==

| Layer No. | Layer Name       | Function Summary                           | Protocols / Devices Example           |
| --------- | ---------------- | ------------------------------------------ | ------------------------------------- |
| 7         | **Application**  | User interface, app-level protocols        | HTTP, FTP, SMTP, DNS                  |
| 6         | **Presentation** | Data translation, encryption, compression  | SSL/TLS, JPEG, MPEG                   |
| 5         | **Session**      | Session management between devices         | NetBIOS, RPC, SQL session             |
| 4         | **Transport**    | Reliable delivery, error checking          | TCP, UDP, Port Numbers                |
| 3         | **Network**      | Routing, logical addressing (IP)           | IP, ICMP, Routers                     |
| 2         | **Data Link**    | Physical addressing (MAC), error detection | MAC Address, Switches, ARP            |
| 1         | **Physical**     | Transmission of raw bits over medium       | Ethernet cables, Hubs, Fiber, Voltage |
## ==🧠 **Physical Layer ==

### 📌 Definition:

The **Physical Layer** is responsible for **transmitting raw bits (0s and 1s)** over a physical medium like copper wire, fiber optics, or air (in the case of wireless).

It **does not understand data or packets**, only electrical/optical/radio signals.

---
### 🧱 Key Functions:

|Function|Description|
|---|---|
|**Bit Transmission**|Converts bits (0s and 1s) into signals (electrical, light, radio) and sends them across the medium.|
|**Physical Topology**|Defines how devices are physically connected (e.g., star, bus, ring).|
|**Synchronization**|Ensures sender and receiver are synchronized for bit-level timing.|
|**Data Rate Control**|Defines transmission rate (e.g., Mbps, Gbps).|
|**Line Configuration**|Point-to-point or multipoint connection.|
|**Transmission Mode**|Simplex, Half-Duplex, Full-Duplex.|

---
### 🔌 Transmission Medium Examples:

|Medium|Description|
|---|---|
|**Twisted Pair**|Used in LAN (e.g., Cat5, Cat6 cables)|
|**Coaxial Cable**|Used in cable TV, broadband internet|
|**Fiber Optic**|Transmits data as light pulses|
|**Wireless**|Uses radio signals (Wi-Fi, Bluetooth)|

---
### 📟 Devices Operate at Physical Layer:

- **Hubs**
    
- **Repeaters**
    
- **Cables**
    
- **Connectors**
    
- **Network Interface Cards (NIC)**

---
### 🔄 Transmission Modes:

|Mode|Description|
|---|---|
|**Simplex**|One-way only (e.g., keyboard to CPU)|
|**Half-Duplex**|Two-way, but one at a time (e.g., walkie-talkies)|
|**Full-Duplex**|Two-way simultaneously (e.g., phones)|

## ==🧷 OSI Layer 2: **Data Link Layer (DLL)** ==

### 📌 Purpose of Data Link Layer:

The Data Link Layer is responsible for the **reliable delivery of data** **between two devices** that are **directly connected** (like your PC and a switch or router on the same LAN). It converts the stream of bits from the **Physical Layer** into **frames** and ensures that they reach the correct device **without errors or collisions**.

---
### 🎯 What exactly does it do?

| Task                      | Description                                                                           |
| ------------------------- | ------------------------------------------------------------------------------------- |
| **Framing**               | Breaks data into manageable chunks called **frames** (like envelopes).                |
| **MAC Addressing**        | Adds **physical (MAC) address** of the sender and receiver to each frame.             |
| **Error Detection**       | Adds checksums like **CRC** (Cyclic Redundancy Check) to detect transmission errors.  |
| **Flow Control**          | Ensures sender doesn’t send faster than the receiver can handle.                      |
| **Medium Access Control** | Ensures multiple devices don’t try to send data at the same time (avoids collisions). |

---

### 🧩 Real Life Analogy:

Imagine you're sending letters:

- **Physical Layer**: Like the post office truck (raw delivery)
    
- **Data Link Layer**: Ensures letter is put into an **envelope**, addressed correctly, sealed, and error-checked before delivery.
---
## 🔍 Sublayers of Data Link Layer

The Data Link Layer is divided into **2 sublayers**:

---
### ==1. ✅ **MAC (Media Access Control) Sublayer**==

|                       |                                                                                      |
| --------------------- | ------------------------------------------------------------------------------------ |
| **Type**              | **48-bit** hardware address (6 bytes), usually shown in **hex**: `00:1A:2B:3C:4D:5E` |
| **Uniqueness**        | Globally unique; assigned by manufacturer                                            |
| **Layers**            | Operates at the **Data Link Layer (MAC Sublayer)**                                   |
| **Used For**          | Device identification within the same **local network** (LAN)                        |
| **Static or Dynamic** | Generally **static**, but can be **spoofed** (changed by software in some cases)     |

|Feature|Explanation|
|---|---|
|**What it does**|Controls **how devices access the network medium** (like Ethernet cable or Wi-Fi signal).|
|**MAC Address**|Uses **MAC addresses** to identify devices uniquely.|
|**Collision Handling**|Prevents and manages **data collisions** (e.g., using **CSMA/CD** or **CSMA/CA**).|
|**Frame Delimiting**|Defines **start and end of frames**.|
|**Error detection**|Adds error-detection info like CRC (does NOT correct it).|

#### 🧠 Example:

In Ethernet, MAC sublayer uses **CSMA/CD**:

- Multiple devices listen before speaking
    
- If two speak at once → collision → both wait random time and try again

---
### 2. ✅ ==**LLC (Logical Link Control) Sublayer**==

|Feature|Explanation|
|---|---|
|**What it does**|Handles **error checking**, **flow control**, and **multiplexing**.|
|**Interface**|Acts as a bridge between **Network Layer (IP)** and **MAC sublayer**.|
|**Frame Synchronization**|Ensures data is received in correct order.|
|**Multiplexing**|Allows multiple protocols (like IP, ARP) to share the same link.|

#### 🧠 Example:

Imagine LLC sublayer is the **secretary** organizing data from different departments (IP, ARP) before handing it off to the **delivery guy** (MAC sublayer).

---
## 🧱 Frame Structure (Simplified)

`+-----------------+--------------+-----------+-------------+-----------+ | Preamble/Start  | Destination  | Source MAC| Data (Payload)| CRC Check| +-----------------+--------------+-----------+-------------+-----------+`

---
### 📦 Summary of Addressing and Data Unit:

|Feature|Layer 2 (Data Link Layer)|
|---|---|
|**Data Unit**|Frame|
|**Address Used**|MAC Address (48-bit)|
|**Devices**|Switch, Bridge, NIC|

---
## 🔄 How a Frame Moves:

Let’s say Computer A sends data to Computer B (same network):

1. The data is prepared by upper layers (like IP packet at Layer 3).
    
2. **DLL adds MAC addresses** (source: A, destination: B) and frames the packet.
    
3. Frame sent via **NIC** → switch checks **destination MAC**.
    
4. Switch forwards frame to correct port → Computer B receives it.
    
5. **CRC check** ensures no error → data passed to upper layers.
---
## 📌 Protocols at Data Link Layer

|Protocol|Usage|
|---|---|
|**Ethernet**|Wired LAN|
|**802.11 (Wi-Fi)**|Wireless LAN|
|**PPP**|Point-to-point (dial-up, VPNs)|
|**HDLC**|High-level Data Link Control for WANs|
|**Frame Relay**|Legacy WAN|
## 🛠 Devices That Work at Data Link Layer:

|Device|Purpose|
|---|---|
|**Switch**|Uses MAC addresses to forward frames|
|**Bridge**|Filters traffic between two network segments|
|**NIC**|Provides interface between computer and network|
## ==🌐 3. Network Layer (Layer 3)==

---
### ✅ **Purpose**:

The **Network Layer** is responsible for:

- **Routing**: Selecting the best physical path for data to travel from source to destination.
    
- **Logical addressing**: Uses **IP addresses** to identify devices on different networks.
    
- **Fragmentation**: Dividing large packets into smaller ones to fit the network MTU.
---
### 📦 **Key Functions**:

|Function|Description|
|---|---|
|**Routing**|Determines the best route across multiple networks.|
|**Logical addressing**|Assigns and uses **IP addresses** to identify devices.|
|**Packet forwarding**|Forwards packets between networks (e.g., LAN to WAN).|
|**Fragmentation & reassembly**|Breaks large packets into smaller fragments based on MTU.|
|**Path determination**|Decides the best path to reach the destination.|

---
### 📬 **Common Protocols in Network Layer**:

- **IP (IPv4 / IPv6)** – Internet Protocol
    
- **ICMP** – Internet Control Message Protocol (used in ping)
    
- **ARP** – Address Resolution Protocol (maps IP to MAC)
    
- **RARP** – Reverse ARP
    
- **IGMP** – Internet Group Management Protocol
    
- **OSPF, BGP, RIP** – Routing protocols
---
### 🎯 **Addressing in this Layer**:

- **IP Addressing**: Every device is assigned a **logical address** (e.g., `192.168.1.1`).
    
- Unlike MAC addresses, IP addresses can **change**, and are **used for routing** across networks.
---
### 🧠 Example:

When you type a website URL:

- Your computer checks DNS for the IP address (e.g., `142.250.77.206`).
    
- The **Network Layer** decides **how to send the packets** to that IP using **routing**.
    
- Routers on the way inspect the packet's **destination IP** and decide the next hop.

---
### 🔀 Devices Operating at Network Layer:
- **Routers** 🚦
- **Layer 3 Switches**

# ==🧱 **Transport Layer (Layer 4)**==

The **Transport Layer** is responsible for **end-to-end communication** between devices. It ensures **reliable** or **unreliable** data delivery, depending on the protocol used (TCP or UDP).

---
## ✳️ Main Responsibilities:

|Feature|Description|
|---|---|
|**Segmentation and Reassembly**|Breaks large data into smaller segments for transmission and reassembles at destination.|
|**Port Numbering**|Uses port numbers to identify source & destination applications.|
|**Connection Management**|Establishes, maintains, and terminates connections (TCP only).|
|**Flow Control**|Prevents overwhelming the receiver using **window size** (TCP).|
|**Error Control**|Ensures data is delivered correctly using **acknowledgments (ACKs)** and **checksums**.|
|**Multiplexing/Demultiplexing**|Allows multiple applications to use the network simultaneously.|

---
## 🔁 **TCP vs UDP**

|Feature|TCP|UDP|
|---|---|---|
|**Type**|Connection-oriented|Connectionless|
|**Reliability**|Reliable (ACK, Retransmission)|Unreliable|
|**Speed**|Slower|Faster|
|**Overhead**|High|Low|
|**Use Case**|Web, Email, File Transfer|Video, DNS, VoIP|

---
## ==🚧 TCP: **Three-Way Handshake**==

Used to **establish a reliable connection** before data is transferred.
### Steps:

1. **SYN** – Client sends SYN (synchronize) to server.
    
2. **SYN-ACK** – Server replies with SYN-ACK.
    
3. **ACK** – Client sends ACK back to server.

`Client        Server   | ---SYN---> |   | <–SYN+ACK– |   | ---ACK---> | Connection Established`

✅ Now data can flow both ways.

---
## 🎯 TCP Segment Structure

Each TCP segment has:

- **Source Port** & **Destination Port**
    
- **Sequence Number**: Position of first byte of data.
    
- **Acknowledgment Number**: Confirms received data.
    
- **Flags**: SYN, ACK, FIN, RST, PSH, URG
    
- **Window Size**: Flow control
    
- **Checksum**: Error checking

---
## 📦 Port Numbers (Most Common)

|Port|Protocol|Service|
|---|---|---|
|20, 21|TCP|FTP (File Transfer Protocol)|
|22|TCP|SSH|
|23|TCP|Telnet|
|25|TCP|SMTP|
|53|UDP/TCP|DNS|
|80|TCP|HTTP|
|110|TCP|POP3|
|143|TCP|IMAP|
|443|TCP|HTTPS|
|3306|TCP|MySQL|
|3389|TCP|RDP|

📝 Port ranges:

- 0–1023: **Well-Known Ports**
    
- 1024–49151: **Registered Ports**
    
- 49152–65535: **Dynamic/Private Ports**

---
## 🧩 Flow Control (TCP)

Prevents data overflow at the receiver side.

- **Sliding Window**: Sender sends data up to window size; waits for ACK before sending more.
    
- Receiver can adjust window size in real-time.
---
## 📛 Error Control (TCP)

- Uses **checksums** to detect errors.
    
- If segment is corrupted → dropped and retransmitted.
    
- **ACKs** confirm receipt.
    
- **Timeouts** trigger retransmission.

## ✂️ Segmentation & Reassembly

- Large messages are divided into **segments** (e.g., 1500 bytes per segment).
    
- Segments are numbered using **sequence numbers**.
    
- Receiver uses these numbers to **reorder** and reassemble.

---
## 🧃 Multiplexing / Demultiplexing

- Multiple apps on one host can communicate using different **port numbers**.
    
- Example:
    
    - Web browser uses port **80**
        
    - SSH uses port **22**

### ==✅ **Session Layer **==

**👉 What it does:**  
The **Session Layer** is responsible for **establishing, managing, and terminating communication sessions** between two devices.

---
### 🔹 **Key Points to Say in Interview:**

- It helps in **starting, maintaining, and ending** sessions between applications.
    
- It provides **dialog control** — deciding who sends data and when (half/full duplex).
    
- It adds **synchronization points** (checkpoints) to resume communication if interrupted.
    
- It makes sure **data flows in an organized way** between applications.
    
---
### 🧠 **Simple Real-Life Example:**

> When you log in to a remote desktop or a video call, the session layer ensures that the session is created, maintained during the call, and properly closed when you disconnect.

---
### 🔗 **Protocols Examples:**

- RPC (Remote Procedure Call)
## ==✅ **Presentation Layer **==

### 👉 What it does:

The **Presentation Layer** is responsible for the **translation, encryption/decryption, and compression** of data.  
It acts like a **translator between application and network**.

---

### 🔹 **Key Responsibilities:**

1. **Translation:**  
    Converts data from application layer format (like text, images) to a format that the network understands — and vice versa.
    
2. **Encryption & Decryption:**  
    Ensures data privacy and security by encrypting before sending and decrypting after receiving.
    
3. **Compression & Decompression:**  
    Reduces data size for faster transmission, especially for media files or large data transfers.
---

### 🧠 **Simple Real-Life Example:**

> When you watch a video on YouTube, the Presentation Layer helps by **decompressing** and **converting** the streamed data into video + sound on your screen.

---

### 🔗 **Protocols & Standards Examples:**

- JPEG, MPEG (Multimedia formats)
    
- SSL/TLS (Secure communication)
    
- ASCII, EBCDIC (Text encoding)
    
- GIF, PNG (Image formats)
## ==✅ **Application Layer**==

### 👉 What it does:

The **Application Layer** is where **end-user interaction happens**.  
It provides **network services directly to the user's applications** (like browsers, email clients, etc.).

---
### ==✅ **What is TLS/SSL?**==

- **TLS (Transport Layer Security)** and **SSL (Secure Sockets Layer)** are **security protocols** that encrypt data during transmission.
    
- **TLS is the successor of SSL**. SSL is now deprecated (TLS 1.3 is the latest as of now).
    
- They ensure:
    
    - 🔒 **Confidentiality** (data is private)
        
    - ✅ **Integrity** (data is not changed)
        
    - 🧾 **Authentication** (you know who you're talking to)
        

---
### 📍 **Where is TLS used?**

- Layer: **Transport Layer (Layer 4 – sometimes viewed as Layer 5 in OSI depending on interpretation)**
    
- Used in:
    
    - HTTPS websites (🔒 in browser)
        
    - Email protocols (SMTP, IMAP, POP3)
        
    - VPNs
        
    - Messaging apps
        
    - VoIP
        

---
### 🔁 **TLS Handshake Steps (Simplified)**

1. **Client Hello**
    
    - Browser says: “Hello, I want to talk securely. Here are the encryption types I support. Here’s a random number.”
        
2. **Server Hello + Certificate**
    
    - Server replies: “Okay! I choose this encryption. Here’s my digital certificate with my public key.”
        
3. **Client Verifies Certificate**
    
    - Browser checks if the certificate is:
        
        - Valid
            
        - Trusted (issued by a trusted CA)
            
        - Not expired
            
4. **Key Exchange**
    
    - Browser creates a secret session key
        
    - Encrypts it using the server’s **public key**
        
    - Sends it to the server
        
5. **Server Decrypts**
    
    - Server uses its **private key** to decrypt the session key
        
6. **Both sides now share the same secret key**
    
    - All communication is now encrypted using **symmetric encryption** (faster than asymmetric)
        
---

### 🛒 **Real-Life Example: Amazon Purchase (HTTPS)**

1. You visit `https://www.amazon.com`
    
2. Your browser and Amazon do the **TLS handshake**
    
3. Your browser receives Amazon’s **digital certificate**
    
4. It **verifies** the certificate is valid and trusted
    
5. Your browser sends a **random key**, encrypted using Amazon’s public key
    
6. Amazon decrypts it, and now both share the **same symmetric session key**
    
7. All future data (login, payment, address) is **securely encrypted**

---
### 🛡️ **Benefits of TLS**

|Feature|Description|
|---|---|
|🔐 Encryption|Protects against eavesdropping|
|🧾 Authentication|Validates the server’s identity|
|🔁 Integrity|Ensures data hasn’t been modified in transit|
|📈 Performance|TLS 1.3 is fast & efficient (0-RTT supported)|

#### ✅ What is it?

The ==**Loopback address**== is a special IP address used by a computer to **send network traffic to itself**.

- **Default loopback address**: `127.0.0.1`
    
- **Hostname**: `localhost`

## ==📘 1. IP Addressing Basics==

An **IPv4 address** is a 32-bit address, written in **dotted decimal** format (e.g., `192.168.1.1`). It consists of:

`Network Portion | Host Portion`

Example:

- `192.168.1.1/24` →
    
    - Network: `192.168.1.0`
        
    - Host range: `192.168.1.1` to `192.168.1.254`
        
    - Broadcast: `192.168.1.255`
        

---

## ==📘 2. IP Classes==

|Class|Range|Default Subnet Mask|Usage|
|---|---|---|---|
|A|1.0.0.0 - 126.0.0.0|255.0.0.0 (/8)|Large networks|
|B|128.0.0.0 - 191.255.0.0|255.255.0.0 (/16)|Medium networks|
|C|192.0.0.0 - 223.255.255.0|255.255.255.0 (/24)|Small networks|

---
## ==📘 3. What is Subnetting?==

Subnetting is the process of dividing one large network into smaller ones.  
Useful when you want to create multiple logical networks or control broadcast domains.

Reduce Ip wastage and improve security & scalability.

---
## 🧮 4. How to Calculate Subnetting (Step-by-Step)

### ✅ Example: `192.168.0.0/24`, and you need at least **48 hosts**.

---
### Step 1: Formula to calculate number of hosts


`2^n - 2 ≥ Required hosts`  

- We try values of `n`:
    
    - `2^5 = 32 - 2 = 30` ❌ too small
        
    - `2^6 = 64 - 2 = 62` ✅
        

So, **6 bits for hosts**  
Remaining: `32 - 6 = 26` bits for Network

📌 So, **New Subnet Mask: `/26` → 255.255.255.192**

---
### Step 2: Find how many subnets you can create from /24 to /26


`New bits used for subnetting = 26 - 24 = 2   2^2 = 4 subnets`

---

### Step 3: Subnet Ranges

Each subnet size:


`2^6 = 64 IPs (including network + broadcast)   → 64 IP blocks each`

- Subnet 1:
    
    - Network: `192.168.0.0`
        
    - Host Range: `192.168.0.1` – `192.168.0.62`
        
    - Broadcast: `192.168.0.63`
        
- Subnet 2:
    
    - Network: `192.168.0.64`
        
    - Host Range: `192.168.0.65` – `192.168.0.126`
        
    - Broadcast: `192.168.0.127`
        
- Subnet 3:
    
    - Network: `192.168.0.128`
        
    - Host Range: `192.168.0.129` – `192.168.0.190`
        
    - Broadcast: `192.168.0.191`
        
- Subnet 4:
    
    - Network: `192.168.0.192`
        
    - Host Range: `192.168.0.193` – `192.168.0.254`
        
    - Broadcast: `192.168.0.255`
        

✅ Each supports up to **62 hosts**

---
## 🧪 Another Example (Try Yourself)

**Given:** `192.168.10.0/24`  
**Required Hosts per Subnet:** 80

1. `2^7 = 128 - 2 = 126` ✅ → use 7 bits for hosts
    
2. `32 - 7 = 25` → Subnet Mask: `/25` → 255.255.255.128
    
3. Subnet size = 128 IPs
    
4. Number of subnets = `2^(25-24) = 2`
    

Subnet 1:

- Network: `192.168.10.0`
    
- Host range: `192.168.10.1` to `192.168.10.126`
    
- Broadcast: `192.168.10.127`
    
Subnet 2:

- Network: `192.168.10.128`
    
- Host range: `192.168.10.129` to `192.168.10.254`
    
- Broadcast: `192.168.10.255`
    

---
## 📓 Summary of Key Formulas

- **Hosts Needed → Host Bits**

    `2^n - 2 ≥ required hosts`
    
- **New Subnet Mask:**

    `32 - host bits = new subnet mask (/n)`
    
- **Subnet Count:**

    `2^(new subnet bits) = total subnets`
    
- **Block Size:**
    
    `256 - subnet mask value in last octet`
    
### ✅ Why We Use ==CIDR== (Classless Inter-Domain Routing)

CIDR is used to make **IP address allocation** and **routing** more **efficient** and **flexible** than the old classful system.

---
### 🔹 1. **Avoid Wastage of IP Addresses**

- In the old system (Class A/B/C), large blocks were assigned even if you didn't need that many.
    
- Example: Class B gave you 65,000+ IPs — even if you needed only 1,000.
    
- **CIDR allows allocation like /22, /27**, so you get only what you need.

---
### 🔹 2. **Route Aggregation (Supernetting)**

- ISPs can advertise **a single summary route** (e.g., `192.0.0.0/16`) instead of thousands of smaller routes.
    
- This reduces the size of routing tables in the Internet backbone → **better performance**.

---
### 🔹 3. **Supports VLSM (Variable Length Subnet Masking)**

- You can create subnets of different sizes in the same network.
    
- Example:
    
    - One subnet: `/24` for 254 hosts
        
    - Another: `/30` for just 2 hosts
        
- **Saves IPs and improves design.**
## ==🌐 Public vs Private IP: Key Differences==

| Feature                  | Private IP                                     | Public IP                    |
| ------------------------ | ---------------------------------------------- | ---------------------------- |
| **Scope**                | Local network only                             | Global Internet              |
| **Routable on Internet** | ❌ No                                           | ✅ Yes                        |
| **Address Ranges**       | 10.x.x.x, 172.16.x.x – 172.31.x.x, 192.168.x.x | Outside private blocks       |
| **Uniqueness**           | Unique only within local LAN                   | Globally unique              |
| **Assigned By**          | Router or Admin (DHCP or static)               | ISP / Internet registry      |
| **Security Risk**        | Lower (not directly exposed)                   | Higher (public visibility)   |
| **Internet Access**      | Requires NAT (router translates)               | Direct communication allowed |
### ==🔁 **What is a Router?**==

A **router** is a network device that forwards data packets between computer networks. It connects multiple networks together, typically a local network (LAN) to the internet (WAN).

- Operates at **Layer 3** (Network Layer) of the **OSI model**.
    
- Uses **IP addresses** to route traffic.
    
- Maintains a **routing table** to decide the best path for packet delivery.
### ==✅ **Router Booting Process==

🧠 **Acronym:** `POST → ROM → RAM → NVRAM → Config`

---
### 🔹 1. **POST (Power-On Self-Test)**

- Checks hardware components (like RAM, interfaces) are working.
    
- If any hardware issue → you’ll get error messages.

---
### 🔹 2. **ROM (Read-Only Memory)**

- Contains **bootstrap program**.
    
- Its job is to **locate and load the IOS** (Operating System).

---
### 🔹 3. **RAM (Random Access Memory)**

- Temporary memory.
    
- Loads the **IOS image** into RAM.
    
- Also stores the **running configuration**.

---
### 🔹 4. **NVRAM (Non-Volatile RAM)**

- Stores **startup configuration** (what to load after boot).
    
- If no config found, router enters **setup mode**.

---
### 🔹 5. **Config (Apply Configuration)**

- If startup-config found → loads into **running config**.
    
- If not found → asks for basic setup manually.

---
### 🧠 Instant Recall Tip:

> **"POST checks hardware, ROM finds IOS, RAM loads it, NVRAM gives config, and router is ready."**

---
### ✅ **==Routing==**

**Routing** is the process of **selecting a path** for traffic in a network, or between multiple networks. It ensures that **data packets** travel from the **source** to the **destination** efficiently.

![[Pasted image 20250805202021.png]]
## ==📦 1. What is **Static Routing**?==

Static Routing is a **manual method** of configuring routing paths in a router. The **network administrator** manually enters routes into the routing table.

### 🔹 Characteristics:

- Admin manually defines route (IP, subnet, next-hop)
    
- Doesn’t change automatically if the network changes
    
- **Low CPU/RAM usage** (no routing protocol needed)
    
- **Secure & predictable**
    
- **Best for small or stable networks**
    

### ✅ Static Route Command (Cisco Example):

`ip route <destination-network> <subnet-mask> <next-hop-IP>`

📌 Example:

`ip route 192.168.2.0 255.255.255.0 192.168.1.2`

---
## 🧩 2. **Types of Static Routing**

|Type|Description|Use Case|
|---|---|---|
|✅ **Standard Static Route**|Basic route manually entered|Small networks|
|🌐 **Default Static Route**|Used when destination is unknown  <br>(like a gateway of last resort)|Internet access, unknown networks|
|🪜 **Floating Static Route**|Backup route with **higher AD (Administrative Distance)**  <br>Overrides only if dynamic route fails|Failover mechanism|
|📶 **Next-Hop Static Route**|Specifies only the **next hop IP address**|Standard practice|
|🧭 **Fully Specified Static Route**|Includes both next hop and exit interface|For better control/performance|
## ==📘 ARP (Address Resolution Protocol)==
ARP is a protocol used to **resolve an IP address to a MAC address** in a **local network (LAN)**.  
It is essential because devices need **MAC addresses** to communicate at the **Data Link Layer (Layer 2)**.

---
### 🔸 Why ARP is Needed

- IP address alone **is not enough** to send packets on Ethernet.
    
- Ethernet (Layer 2) requires **MAC address** to forward frames.
    
- So if we know the **IP address** but not the **MAC address**, ARP helps us find it.
    
---
### 🔸 Where ARP is Used

- Only within a **local network (LAN)** or **same subnet**.
    
- For **inter-network communication**, the packet goes to the **default gateway**, and ARP resolves the MAC of the **gateway/router**.
    

---
### 🔸 Which Layer Does ARP Work On?

- ARP operates between:
    
    - **Layer 2 (Data Link)** and
        
    - **Layer 3 (Network)**  
        ✅ Often called a **Layer 2.5 protocol**.
        

---
### 🔸 How ==ARP Works== (Steps)

1. Host A wants to communicate with Host B (knows IP, not MAC).
    
2. Host A checks its **ARP cache** for an entry.
    
3. If not found, sends **ARP request** (broadcast):
    
    `Who has 192.168.1.5? Tell 192.168.1.2`
    
4. Target host (192.168.1.5) replies with **ARP reply** (unicast):

    `192.168.1.5 is at AA:BB:CC:DD:EE:FF`
    
5. Host A stores this in its **ARP table** and uses the MAC to send the packet.

---
### 🔸 ARP Packet Structure

- ARP Request or Reply includes:
    
    - Sender MAC
        
    - Sender IP
        
    - Target IP
        
    - Target MAC (empty in request)

---
### 🔸 ARP Table / Cache

- Stores recently resolved IP-MAC mappings.
    
- OS maintains this table (temporary entries expire).
    
- View command:
    
    - Windows: `arp -a`
        
    - Linux/macOS: `ip neigh` or `arp`
        

---
### 🔸 Types of ARP

|Type|Description|
|---|---|
|**Normal ARP**|Standard IP → MAC resolution|
|**Gratuitous ARP**|A device sends ARP request for **its own IP** to update other ARP tables (e.g., IP conflict detection or failover)|
|**Proxy ARP**|Router replies to ARP request **on behalf of another device**, allowing devices in different subnets to communicate|
|**Reverse ARP (RARP)**|Old method to get IP address from MAC (rarely used today, replaced by DHCP)|
|**Inverse ARP (InARP)**|Used in Frame Relay or ATM to discover IP from known Layer 2 address|

### 🔸 Security Concerns

- **ARP Spoofing/Poisoning**:  
    Attacker sends fake ARP replies to redirect traffic (e.g., Man-in-the-Middle attack).
    
---
### 🔸 ARP vs DNS

|ARP|DNS|
|---|---|
|IP → MAC|Domain name → IP|
|Works at Layer 2.5|Works at Application Layer|
|Only within LAN|Works across Internet|

---
### 🔸 Example Scenario

You want to ping `192.168.1.10`.  
If its MAC isn't in your ARP cache:

- Your device broadcasts an ARP request.
    
- The device with `192.168.1.10` responds with its MAC.
    
- Now your device sends the actual ping packet using that MAC.
## ==🔧 **DHCP (Dynamic Host Configuration Protocol)** ==

DHCP is a **network management protocol** used to **automatically assign IP addresses** and other network configuration parameters (like subnet mask, gateway, DNS) to devices (clients) on a network.
Application layer protocol.
It eliminates the need for **manual IP configuration**.

---
### 🧠 **Why is DHCP Used?**

- Saves time: No manual IP assignment
    
- Avoids conflicts: Prevents duplicate IPs
    
- Enables plug-and-play networking
    
- Easy management of large networks
    
---

### 🔄 **How DHCP Works (Step-by-Step Process)**

> 📌 Known as **DORA Process** (Discover, Offer, Request, Acknowledge)

1. **DHCP Discover (Broadcast)**  
    Client sends a **DHCPDISCOVER** message to find available DHCP servers.
    
2. **DHCP Offer**  
    DHCP server responds with a **DHCPOFFER** (includes IP address, lease time, gateway, DNS, etc.)
    
3. **DHCP Request**  
    Client responds with a **DHCPREQUEST** saying, “I want this IP.”
    
4. **DHCP Acknowledge**  
    Server confirms with a **DHCPACK**, officially assigning the IP address.
    

---
### ⚙️ **What Information DHCP Provides?**

- IP address
    
- Subnet mask
    
- Default gateway
    
- DNS servers
    
- Lease duration
    
- TFTP server (optional)

---
### 📁 **Types of DHCP Allocations**

1. **Dynamic Allocation**  
    IPs are leased from a pool for a limited time.
    
2. **Automatic Allocation**  
    Similar to dynamic, but once assigned, the IP is permanently reserved.
    
3. **Manual Allocation (Static DHCP)**  
    DHCP assigns a specific IP to a MAC address based on admin configuration.
    
---
### ⏳ **DHCP Lease Time**

- Lease time = How long the client can use the assigned IP.
    
- Before expiration:
    
    - **T1 timer** (50%): Client tries to renew IP with the same server.
        
    - **T2 timer** (87.5%): Client tries to renew IP with any DHCP server.
        
    - If all fail, client sends DHCPDISCOVER again.

---
### 📡 **DHCP Message Types**

|Message|Description|
|---|---|
|DHCPDISCOVER|Client broadcasts to find a server|
|DHCPOFFER|Server offers IP configuration|
|DHCPREQUEST|Client requests offered IP|
|DHCPACK|Server acknowledges and assigns IP|
|DHCPNAK|Server rejects the request|
|DHCPDECLINE|Client says offered IP is already in use|
|DHCPRELEASE|Client gives up the IP address|
|DHCPINFORM|Client asks for local config info|

---
### 🗃️ **DHCP Ports**

- **UDP Port 67** – Server listens
    
- **UDP Port 68** – Client sends

### ==🔁 **What is NAT?**==

**NAT (Network Address Translation)** is a process where a **private IP address is translated into a public IP address**, and vice versa. It allows **multiple devices** on a private network to access the internet using a **single public IP**.

It works at the **Network Layer (Layer 3)** of the **OSI Model**.

---

### 🔧 **Why NAT is used**

1. **IPv4 Address Conservation:** Due to a shortage of IPv4 public IPs, NAT allows multiple private IPs to share one public IP.
    
2. **Security:** Internal IPs remain hidden from the external network.
    
3. **Routing Simplification:** NAT helps networks merge without reconfiguring IPs.

---
### 🌐 **Types of NAT**

|Type|Description|Example|
|---|---|---|
|**Static NAT**|One-to-one mapping between private and public IP.|Private 192.168.1.10 → Public 203.0.113.10|
|**Dynamic NAT**|Many private IPs share a pool of public IPs. Mapping is done dynamically.|192.168.1.10 → Any free IP from 203.0.113.10–20|
|**PAT (Port Address Translation)** aka **NAT Overload**|Many private IPs share one public IP using different port numbers.|192.168.1.10:1234 → 203.0.113.10:4001|

🔹 PAT is the most commonly used NAT type.

---

### 📦 **How NAT Works (General Flow)**

1. Internal device sends a packet to the internet.
    
2. NAT device (usually a router or firewall) replaces the **source IP** with its **public IP**.
    
3. Keeps a table mapping:
    
    `Private IP:Port <-> Public IP:Port`
    
4. When the reply comes back, NAT checks the port and sends it back to the original private IP.

---

### 🧠 **NAT Table Example (for PAT)**

|Internal IP:Port|Public IP:Port|
|---|---|
|192.168.1.10:1025|203.0.113.10:4001|
|192.168.1.11:1026|203.0.113.10:4002|

---

### ⚙️ **Static NAT – In Detail**

- **One-to-One Mapping**
    
- Manual configuration
    
- Used for internal servers (like web or mail servers) that need to be reachable from the internet


`ip nat inside source static 192.168.1.10 203.0.113.10`

---
### ⚙️ **Dynamic NAT – In Detail**

- **One-to-One Mapping**, but dynamic
    
- Uses a pool of public IPs
    
- Mapping is temporary and depends on availability


`ip nat pool NATPOOL 203.0.113.10 203.0.113.20 netmask 255.255.255.0 ip nat inside source list 1 pool NATPOOL`

---
### ⚙️ **PAT – Port Address Translation (Overloading)**

- **Many-to-One Mapping**
    
- Maps many private IPs to a single public IP using port numbers
    
- Most common in homes and small offices

`ip nat inside source list 1 interface FastEthernet0/0 overload`

## ==🕰️ **What is NTP?**==

**NTP (Network Time Protocol)** is a protocol used to **synchronize the time** of computers across a network with high accuracy—usually within **milliseconds** of UTC (Coordinated Universal Time).

- **Port**: 123 (UDP)
    
- **Layer**: Application Layer
    
- **Purpose**: Ensures all devices (routers, switches, servers, endpoints) have **accurate and synchronized time** for logs, security, and operations.
    

---

## 📶 **How Does NTP Work?**

NTP uses a **hierarchy of time sources** called **Stratum levels** and a technique called **timestamp exchange** to sync time.

### 📐 NTP Timestamp Process (simplified):

When a client wants to sync with an NTP server, it uses **4 timestamps**:

|Timestamp|Description|
|---|---|
|**T1**|Time request left the client|
|**T2**|Time request received by server|
|**T3**|Time reply sent from server|
|**T4**|Time reply received by client|

From this, the client calculates:

- **Round Trip Delay**
    
- **Clock Offset**

## ==🧭 What is **Distance Vector Routing Protocol**?==

A **Distance Vector Routing Protocol** is a type of dynamic routing protocol that determines the **best path** to a destination based on the **number of hop counts** it takes to reach the next router.
### 📌 Key Concepts:

|Term|Meaning|
|---|---|
|**Distance**|Usually measured in **hop count** (number of routers to reach destination)|
|**Vector**|The **direction or next hop router** to reach the destination|
|**Routing Table**|Each router keeps a table listing the best-known distance and direction to all destinations|
|**Periodic Updates**|Routers **share entire routing tables** with neighbors at regular intervals|
|**Split Horizon / Poison Reverse**|Techniques to prevent routing loops|
### ==🔁 RIP (Routing Information Protocol)==

RIP is the **most basic** distance vector routing protocol.

#### 🔹 How RIP works:

- Every router **sends its routing table** to its neighbors every **30 seconds**.
    
- The **maximum hop count** is **15**. If the destination is 16 hops away, it's **considered unreachable**.
    
- Uses **UDP port 520**.
    
- **Metric**: Hop count.

#### 🔹 RIP Versions:

|Version|Description|
|---|---|
|**RIP v1**|Doesn’t support VLSM (Variable Length Subnet Masking), uses only classful routing|
|**RIP v2**|Supports VLSM and multicast updates|
|**RIPng**|Used for IPv6 routing|

---
### 🔁 Pros of RIP:

- Simple and easy to configure
    
- Low resource consumption
### 🔁 Cons of RIP:

- Very slow convergence
    
- Limited to small networks (due to 15 hop count)
    
- Vulnerable to routing loops

### ==🔍 **What is Link State Routing Protocol?**==
link state protocols build a **complete map of the network** to make routing decisions based on the **state (status) and cost of each link**.
### 📦 **Main Features**

| Feature            | Description                                                             |
| ------------------ | ----------------------------------------------------------------------- |
| Topology Knowledge | Each router knows the entire network's topology (not just neighbors).   |
| Metric Used        | Bandwidth, delay, or other link cost (not hop count).                   |
| Routing Algorithm  | Shortest Path First (SPF) / Dijkstra’s algorithm.                       |
| Convergence        | Faster convergence than distance vector protocols.                      |
| Updates            | Triggered only when there is a change, not periodic.                    |
| Example Protocols  | **OSPF (Open Shortest Path First)**, **IS-IS (Intermediate System–IS)** |
### 🔁 **Working Steps of Link State Routing**

1. **Neighbor Discovery** – Router discovers its directly connected routers.
    
2. **Link-State Advertisement (LSA)** – Router sends LSA to **all routers in the area**.
    
3. **Database Building** – Each router stores received LSAs in a **Link-State Database (LSDB)**.
    
4. **SPF Calculation** – Router runs SPF algorithm to calculate the **best path**.
    
5. **Routing Table Update** – Based on SPF result, the routing table is updated.

### ==📘 Administrative Distance (AD)==

**Administrative Distance (AD)** is a ==**value used by routers to determine which routing protocol to trust the most**== when there are multiple paths to the same destination from different routing sources.

---
### ✅ Why AD is Important:

Imagine your router receives route information from:

- RIP
    
- OSPF
    
- EIGRP  
    ...but **all of them have a path to the same network (e.g., 192.168.1.0/24)**.
    

> **Which one should the router choose?** The one with the **lowest Administrative Distance.**

---

### 🎯 Default Administrative Distances:

|Routing Source|AD Value|
|---|---|
|Directly Connected|0|
|Static Route|1|
|EIGRP|90|
|OSPF|110|
|IS-IS|115|
|RIP|120|
|External EIGRP|170|
|BGP (External)|20|
|BGP (Internal)|200|
|Unknown/Untrustworthy|255 (never used)|

---
### 🔁 Example:

If a router has:

- Route from OSPF to 192.168.1.0/24 (AD 110)
    
- Route from RIP to 192.168.1.0/24 (AD 120)
    

➡️ The router will **choose the OSPF route** because **110 < 120**

---

### ✅ Key Points:

- **Lower AD = More trusted**
    
- AD is only used **when multiple protocols provide routes to the same destination**
    
- It helps routers **avoid routing loops and inconsistencies**

### ==🔐 What is ACL ?==

An **Access Control List (ACL)** is a set of rules used to **filter network traffic** and **control access** to and from devices on a network. It works like a **security filter** on routers or switches.

---
### 💡 Simple Explanation:

Think of an ACL like a **bouncer at a nightclub**:

- It checks who is allowed in (permit)
    
- And who must be denied entry (deny)
    

Each rule in an ACL is a condition:

- ✅ Permit traffic
    
- ❌ Deny traffic
    

---

### 🛠️ Types of ACLs

|Type|Description|
|---|---|
|**Standard ACL**|Filters only by **source IP address**|
|**Extended ACL**|Filters by **source IP, destination IP, protocol, and port**|
|**Named ACL**|ACLs with custom names instead of just numbers|
## ==📘 OSPF – Open Shortest Path First==

### 🔹 Definition:

OSPF is a **link-state routing protocol** used to determine the **best path** for IP packets within a **single autonomous system (AS)**.  
It is an **interior gateway protocol (IGP)** and **uses Dijkstra’s algorithm** to calculate the shortest path.

---

## ✅ Key Features:

|Feature|Description|
|---|---|
|Protocol Type|Link-State|
|Routing Type|Interior Gateway Protocol (IGP)|
|Algorithm Used|Dijkstra’s Shortest Path First (SPF)|
|Metric|Cost (based on bandwidth)|
|Administrative Distance|110|
|Transport Protocol|IP Protocol Number 89|
|Classful/Classless|Classless (supports VLSM, CIDR)|
|Authentication|Supports MD5, Plaintext, or None|
|Multicast Addresses|224.0.0.5 (All OSPF routers), 224.0.0.6 (DR/BDR)|
|Convergence|Fast|
|Scalability|High (supports areas)|

---

## 🧠 OSPF Terminology:

|Term|Description|
|---|---|
|**Router ID**|Unique 32-bit ID (Highest IP or manually assigned)|
|**Area**|Logical group of routers. Backbone is Area 0.|
|**LSA**|Link-State Advertisement (OSPF updates)|
|**LSDB**|Link-State Database (network topology table)|
|**DR/BDR**|Designated Router / Backup DR – reduce traffic on broadcast networks|
|**Neighbor**|Two routers that exchange Hello packets|
|**Adjacency**|Two routers fully synchronized LSDBs|

---

## 🔄 OSPF Packet Types:

|Type|Name|Purpose|
|---|---|---|
|1|Hello|Discover and maintain neighbors|
|2|Database Description (DBD)|Summary of LSDB|
|3|Link-State Request (LSR)|Ask for more recent LSAs|
|4|Link-State Update (LSU)|Sends requested LSAs|
|5|Link-State Acknowledgement|Confirms LSA received|

---

## 📶 OSPF States (Neighbor Formation):

|State|Description|
|---|---|
|**Down**|No Hello received|
|**Init**|Hello sent but no response|
|**2-Way**|Hello received with own Router ID|
|**ExStart**|Start of database exchange|
|**Exchange**|DBD packets exchanged|
|**Loading**|Routers request missing LSAs|
|**Full**|LSDBs fully synchronized|

---

## 🏢 OSPF Areas:

- **Backbone Area (Area 0):** Central area; all other areas must connect to this.
    
- **Regular Area:** Normal area with full LSDB.
    
- **Stub Area:** No external routes allowed; uses default route.
    
- **Totally Stubby Area:** Blocks external and inter-area routes.
    
- **NSSA (Not-So-Stubby Area):** Allows external routes in a limited way.
    

---
### ==🌐 **OSPF in 5 Simple Steps (Easy to Explain)**==

1. **Area Assignment (Usually Area 0)**  
    All OSPF routers must connect to a backbone area (Area 0) directly or indirectly. This helps organize the network.
    
2. **Hello Packets → Forming Neighbors**  
    Routers send **Hello messages** to discover and build relationships with nearby routers (neighbors).
    
3. **Exchange of LSAs (Link-State Advertisements)**  
    Routers share info about their links with neighbors via LSAs, which helps every router learn the **full network topology**.
    
4. **Build the Same LSDB (Link-State Database)**  
    All routers maintain a **common network map** in memory called LSDB, ensuring consistency.
    
5. **SPF Algorithm (Shortest Path First)**  
    Each router runs **Dijkstra’s algorithm** on the LSDB to find the **best (shortest) path** to every network.
    
6. **Update Routing Table**  
    The final best paths are saved in the **routing table** for actual data forwarding.
## 🔧 How ==OSPF Works== (Step-by-Step):

### **1. Router Initialization**

When a router running OSPF boots up:

- It checks all its interfaces and enables OSPF on configured ones.
    
- Each interface is assigned to an **OSPF area** (e.g., Area 0 is the backbone).

---
### **2. Hello Protocol (Neighbor Discovery)**

Routers send **Hello packets** on OSPF-enabled interfaces to discover neighbors.

- These Hello packets are sent to multicast IP `224.0.0.5`.
    
- Parameters in Hello:
    
    - Router ID
        
    - Hello/dead interval
        
    - Area ID
        
    - Authentication (if any)
        
- If two routers agree on the Hello parameters → they become **neighbors**.

---
### **3. Adjacency Formation**

Not all neighbors form **full adjacencies**.

- On broadcast/multicast networks (e.g., Ethernet), OSPF elects:
    
    - **DR (Designated Router)**
        
    - **BDR (Backup Designated Router)**
        
- DR/BDR reduce traffic by centralizing LSAs.

---
### **4. Database Description (DBD) Exchange**

Once adjacency is formed:

- Routers exchange **Database Description (DBD)** packets.
    
- Each DBD packet summarizes known networks (LSAs).
    
- This ensures both routers have consistent **Link State Databases (LSDBs)**
---
### **5. Link-State Request/Update**

If a router detects a newer or unknown LSA from a neighbor’s DBD:

- It sends a **Link-State Request (LSR)**.
    
- The neighbor responds with a **Link-State Update (LSU)**.
    
- This process continues until both routers have synced LSDBs.
---
### **6. SPF Calculation**

Once the LSDB is updated:

- Each router runs the **Shortest Path First (SPF)** algorithm (Dijkstra's algorithm).
    
- This builds the **Shortest Path Tree (SPT)**.
    
- The SPT determines the **best paths** to each network and updates the **routing table**.
---
### **7. Route Installation**

The calculated best routes are installed in the router's routing table:

- Route entries include metrics (cost), next-hop IP, and outgoing interface.

---
## ⚙️ OSPF Cost (Metric):

`Cost = Reference Bandwidth / Interface Bandwidth  (Default Reference Bandwidth = 100 Mbps)`

|Bandwidth|Cost|
|---|---|
|100 Mbps|1|
|10 Mbps|10|
|1 Gbps|0.1 (rounded to 1)|

> Lower cost = better path.

---

## 🛡️ OSPF Authentication:

|Type|Description|
|---|---|
|None|No authentication|
|Plaintext|Simple password in Hello packets|
|MD5|Encrypted hash-based authentication|

---

## 🔄 OSPF Tables:

|Table|Purpose|
|---|---|
|Neighbor|List of discovered neighbors|
|Topology (LSDB)|Complete OSPF network map|
|Routing|Best paths based on SPF|
## ==🌐 What is EIGRP?==

**EIGRP** is a **Cisco proprietary** **advanced distance vector routing protocol**. It’s faster and smarter than RIP and combines the advantages of **both distance vector and link-state** protocols.

---
### ==📘 **EIGRP (Enhanced Interior Gateway Routing Protocol) – Easy 5-Step Explanation**==

---

#### ✅ 1. **Neighbor Discovery**

EIGRP sends **Hello packets** to discover and maintain relationships with directly connected routers (neighbors).

---

#### ✅ 2. **Exchange Routing Information**

Once neighbors are formed, routers **exchange routing tables** containing route information like bandwidth, delay, etc.

---

#### ✅ 3. **DUAL Algorithm (Diffusing Update Algorithm)**

This is EIGRP’s brain. It selects the **best path** (Successor) and also keeps a **backup path** (Feasible Successor) ready for quick failover — **no recalculation needed** like OSPF.

---

#### ✅ 4. **Update Routing Table**

The **best routes (lowest metric)** are added to the routing table. If the primary route fails, EIGRP instantly switches to the backup.

---
#### ✅ 5. **Triggered Updates Only (Not Periodic)**

EIGRP sends **updates only when there is a change**, not every 30 seconds like RIP — saving bandwidth and making it faster.

---
## 🔧 How EIGRP Works (Step-by-Step)

### 1. **Neighbor Discovery (Hello Protocol)**

- Routers send **Hello packets** to discover and maintain neighbor relationships.
    
- Hello packets are sent to **multicast IP `224.0.0.10`**.
    
- If a router responds, they form an **EIGRP neighbor adjacency**.
    

📌 **Why?** Routers must become neighbors before they exchange routing info.

---

### 2. **Reliable Update of Routing Information**

- After neighbors are formed, routers **exchange full routing tables** using **Update packets**.
    
- EIGRP uses **reliable transport** to ensure data is delivered properly.
    

---

### 3. **Topology Table Formation**

- Every router builds a **topology table**.
    
- This contains all possible routes to all destinations learned from its neighbors.
    
- Each route includes:
    
    - **Metric (cost)**
        
    - **Bandwidth**
        
    - **Delay**
        
    - **Load**
        
    - **Reliability**
        

📌 EIGRP uses a **composite metric** (not just hop count like RIP).

---
### 4. **DUAL Algorithm – Core of EIGRP**

The **Diffusing Update Algorithm (DUAL)** decides the best loop-free path.

It identifies:

#### ✅ Successor

- The **best route** (lowest cost) to reach a destination.
    
- Installed in the **routing table**.

#### 🔁 Feasible Successor

- A **backup route** (next-best route) that is loop-free and ready to use instantly if the primary path fails.
    

> 💡 **DUAL prevents routing loops and ensures fast convergence**.

---
### 5. **Routing Table Update**

- EIGRP selects the **Successor** (best path) from the Topology Table and adds it to the **Routing Table**.
    
- If a primary route fails, the **Feasible Successor** is promoted immediately without recalculation.

---
### 6. **Partial & Bounded Updates**

- Unlike RIP, EIGRP does **not send full updates periodically**.
    
- It only sends updates **when there is a change**, and **only to affected routers**.
    

📌 This saves **bandwidth and CPU**.

---

## 📊 EIGRP Metrics (How it Calculates Best Path)

EIGRP metric formula uses:

- **Bandwidth**
    
- **Delay**
    
- **Load**
    
- **Reliability**
    
- **MTU** (not part of metric but exchanged)
    

Default formula:  
`Metric = (10^7 / Bandwidth) + Delay`

---

## ✅ Advantages of EIGRP

|Feature|Benefit|
|---|---|
|Fast convergence|Uses DUAL|
|Loop-free paths|Guaranteed via Feasible Successor|
|Scalable|Handles large networks well|
|Supports VLSM/CIDR|Classless protocol|
|Load balancing|Equal & unequal cost|

---
## ❗️EIGRP Packet Types

|Packet|Use|
|---|---|
|Hello|Discover neighbors|
|Update|Send routing info|
|Acknowledgment (ACK)|Confirm receipt|
|Query|Ask for alternative routes|
|Reply|Answer to Query|

---
## 🔒 Administrative Distance (AD)

- EIGRP has an AD of:
    
    - **90** for internal routes (within same AS)
        
    - **170** for external routes (redistributed)

## ==🧠 What is BGP?==

**BGP (Border Gateway Protocol)** is the **main routing protocol of the Internet**. It connects **different networks (Autonomous Systems)** and helps them **share route information**.

- BGP is a **path vector routing protocol**
    
- It is used **between ISPs** and also **within large enterprises**
    
- BGP runs over **TCP port 179**

---
## 🔄 Types of BGP

|Type|Description|
|---|---|
|**eBGP**|External BGP – between different Autonomous Systems (e.g., ISP to ISP)|
|**iBGP**|Internal BGP – within the same AS (used inside large networks/companies)|

---

## 🔍 Step-by-Step: **How ==BGP Works==**

### 1. **BGP Peer Establishment**

- Routers (BGP speakers) form a **TCP connection on port 179**
    
- Called **neighbors** or **peers**
    
- Exchange **OPEN** messages to establish the session

---
### 2. **Exchange of Routes (NLRI)**

- After the connection is up, routers exchange:
    
    - **NLRI** = Network Layer Reachability Information (i.e., what IP prefixes/networks they can reach)
        
    - Attributes for each route
---
### 3. **Route Advertisement**

- Routers **advertise only the best routes** to neighbors
    
- They do **incremental updates**, not full tables each time
    
- Routes are **withdrawn** if they become unreachable
---
### 4. **BGP Attributes (Very Important!)**

These are **used to choose the best path** when multiple options are available:

|Attribute|Description|
|---|---|
|**Weight**|Cisco-only. Highest wins. Locally set, not shared with others|
|**Local Preference**|Used inside AS. Highest wins. Default is 100|
|**AS Path**|Shows list of ASes a route passed. Shortest path preferred|
|**Origin**|How the route was learned: IGP > EGP > Incomplete|
|**MED**|Multi Exit Discriminator – lower is better. Used to influence inbound traffic|
|**eBGP over iBGP**|Prefer external routes to internal ones|
|**Router ID**|Lowest router ID wins as a last tiebreaker|

---
### 5. **Best Path Selection Algorithm**

BGP uses the following **order of preference**:

`1. Highest Weight (Cisco) 2. Highest Local Preference 3. Shortest AS Path 4. Lowest Origin Type (IGP < EGP < Incomplete) 5. Lowest MED 6. Prefer eBGP over iBGP 7. Lowest IGP metric to next-hop 8. Oldest route (for stability) 9. Lowest Router ID`

---
### 6. **Routing Table Update**

- BGP selects the **best route** and installs it in the **RIB (Routing Information Base)**
    
- Then shares that route with its **other neighbors**
---
## 🔐 BGP Security (Basic Overview)

BGP was not originally secure. Some issues:

- Route hijacking
    
- Prefix leaks
    

**Modern solutions**:

- **RPKI (Resource Public Key Infrastructure)**
    
- **BGP Filtering**
    
- **Prefix-lists, route-maps, and max-prefix limits**
    

---

## 🌐 Real-World Example

|ISP A (AS 100)|⇄ BGP ⇄|ISP B (AS 200)|
|---|---|---|
|192.168.0.0/16 route|⬅️➡️|announces 10.0.0.0/8|
|BGP shares prefix + AS|||
|Adds AS Path, e.g.||200 → 100|

---

## 🔁 Summary

|Feature|Description|
|---|---|
|Protocol Type|Path vector protocol|
|Transport Protocol|TCP (port 179)|
|Metric Used|BGP Attributes|
|Convergence Speed|Slower compared to IGPs|
|Loop Prevention|AS-Path attribute|
|Used For|Inter-AS (between ISPs), large-scale enterprises|
## ==🧠 What is Switching?==

**Switching** is the process of directing network traffic between devices on the **same network (LAN)**. Switches operate at **Layer 2 (Data Link Layer)** of the OSI model, although some Layer 3 (network layer) switches also exist.

Switching involves:

- Receiving a frame
    
- Examining its destination MAC address
    
- Forwarding it to the correct port (based on MAC address table)

### How a Switch Learns MAC Addresses (Step-by-Step)

When a switch is **powered on**, its **MAC Address Table (CAM Table)** is **empty**.

Now suppose we connect multiple devices to the switch:

---
### 📶 Scenario Example:

Let’s say:

- **PC A** is connected to **Port 1**
    
- **PC B** is connected to **Port 2**
    
- **PC A wants to send data to PC B**

---
### 🔍 Step-by-Step Working:

#### ✅ Step 1: Frame Sent

- PC A sends a frame to PC B.
    
- The **frame contains:**
    
    - **Source MAC**: MAC address of PC A
        
    - **Destination MAC**: MAC address of PC B
---
#### ✅ Step 2: Switch Checks MAC Table

- Switch checks its **MAC address table (CAM table)**:
    
    - Does it **know where the destination MAC (PC B)** is?
        
        - If **NO**, it **floods the frame** out to all ports **except** the one it came from.
            
---
#### ✅ Step 3: Switch Learns Source MAC

- Even though it doesn’t know PC B’s MAC yet,
    
- The switch sees the **source MAC address** of the frame (from PC A),
    
- It **records the MAC and the port** it came from in the MAC table:

    `MAC Table: MAC-A → Port 1`
    
---
#### ✅ Step 4: PC B Receives the Frame

- PC B receives the frame (because of flooding).
    
- PC B now responds to PC A.

---
#### ✅ Step 5: Switch Learns PC B’s MAC

- Now, the **response from PC B to PC A** is sent.
    
- This time, the frame has:
    
    - **Source MAC**: PC B’s MAC
        
    - **Destination MAC**: PC A’s MAC
        
- The switch **learns PC B’s MAC address** and updates its table:

    `MAC Table: MAC-A → Port 1   MAC-B → Port 2`
    
---
### 🧠 Summary:

- Switch **learns MAC addresses** by watching the **source MAC addresses** of incoming frames.
    
- It builds a **MAC address table (CAM table)** to forward traffic efficiently without flooding.
    
- If a destination MAC is unknown, it **floods**, and **learns during the response.**

### 🔁 **What is a Loop in Networking (Switching Loop)?**

A **switching loop** (or **network loop**) occurs **when there are multiple active paths between two or more switches**, and **no loop prevention mechanism** is in place. This causes Ethernet frames to **circulate endlessly**.

---

### ⚠️ Why Loops Are a Problem?

1. **Broadcast Storms**: A broadcast frame is forwarded endlessly between switches, consuming all bandwidth.
    
2. **MAC Table Instability**: Switches keep learning and relearning incorrect MAC address locations.
    
3. **High CPU Utilization**: The switch has to process the same packets repeatedly.
    
4. **Network Outage**: Legitimate traffic gets dropped or delayed, resulting in partial or complete network failure.
    

---

### 💡 How It Happens – Example:

Suppose you have 3 switches:

- **Switch A**
    
- **Switch B**
    
- **Switch C**
    

They are connected in a **triangle topology**, like this:


`A ----- B  \     /    \ /     C`

If a broadcast frame is sent (e.g., ARP request), it goes:

- From A → B → C → A → B → C … and never stops.
    

Since **Ethernet doesn’t have a Time-To-Live (TTL)** like IP packets, the frame never expires. That’s a **loop**.

---

### 🔒 How to Prevent Loops?

✅ **Spanning Tree Protocol (STP)** or its improved versions like:

- **RSTP** (Rapid Spanning Tree Protocol)
    
- **MSTP** (Multiple Spanning Tree Protocol)
    

These protocols:

- Elect a **Root Bridge**
    
- Block redundant ports
    
- Ensure there's only **one active path** between any two switches.

## ==📘 VLAN (Virtual Local Area Network) – Notes==

### ✅ Definition:

- VLAN is a **logical grouping of devices** within a network, regardless of their physical location.
    
- It operates at **OSI Layer 2** (Data Link Layer).
    
- Used to **segregate broadcast domains** within a switch.
---
### 🎯 Key Purposes:

- Improve **network performance**
    
- Enhance **security**
    
- Reduce **broadcast traffic**
    
- Enable **logical grouping** of users (e.g., by department)
---
### 🧠 How it Works:

- VLAN assigns each switch port to a **VLAN ID**.
    
- Devices in the **same VLAN can communicate** directly.
    
- Devices in **different VLANs need a router** (or Layer 3 switch) to communicate — called **Inter-VLAN routing**.

---
### 🧱 Types of VLANs:

|Type|Description|
|---|---|
|**Default VLAN**|VLAN 1 — All switch ports are in this by default.|
|**Data VLAN**|Used to carry user-generated traffic.|
|**Voice VLAN**|Used to carry VoIP traffic (higher priority).|
|**Management VLAN**|Used for switch administration (e.g., VLAN 99).|
|**Native VLAN**|Used for untagged traffic on a trunk port.|

---
### 🔗 VLAN Port Types:

|Port Type|Description|
|---|---|
|**Access Port**|Connects to end devices (PCs, printers); carries traffic for **one VLAN**.|
|**Trunk Port**|Connects to other switches/routers; carries **multiple VLANs** using **802.1Q tagging**.|

---
### 📌 Important Terms:

- **VLAN ID**: Number (1–4094) used to identify a VLAN.
    
- **802.1Q**: Standard for VLAN tagging on trunk links.
    
- **Broadcast domain**: VLAN creates separate broadcast domains.
---
### 🖥️ Example:

|Device|Port|VLAN ID|Purpose|
|---|---|---|---|
|PC1|fa0/1|10|HR|
|PC2|fa0/2|20|Finance|
|PC3|fa0/3|30|IT|

- Each VLAN is **isolated**.
    
- To allow communication between VLAN 10 and 20, you need a **router or L3 switch**.
---
### ⚙️ VLAN Configuration Example (Cisco CLI):

`Switch(config)# vlan 10 Switch(config-vlan)# name HR Switch(config)# interface fa0/1 Switch(config-if)# switchport mode access Switch(config-if)# switchport access vlan 10`

---
### 🚀 Benefits of VLAN:

- Better **security** by isolating sensitive traffic
    
- Easier **management** of large networks
    
- Reduces unnecessary **broadcasts**
    
- Supports **logical network design** (department-wise)

## ==🌐 What is STP?==

**STP (Spanning Tree Protocol)** prevents **loops** in Layer 2 Ethernet networks by creating a **loop-free logical topology**. It's defined in **IEEE 802.1D**.

---

## 🔄 STP: Step-by-Step Working (with Root Port selection in detail)

### **Step 1: Elect the Root Bridge (Main switch)**

- Each switch sends **BPDU** (Bridge Protocol Data Units) containing:
    
    - **Bridge ID (BID)** = **Priority + MAC address**
        
- The switch with the **lowest BID** becomes the **Root Bridge**.
    
    - If all priorities are default (32768), the switch with the **lowest MAC address** becomes Root.
        

---

### **Step 2: Select Root Port (RP) – This is the key part you asked**

👉 The **Root Port** is the **best path to reach the Root Bridge** from a non-root switch.
#### 🔍 How is the Root Port chosen?

Each non-root switch compares **received BPDUs** on all its ports.

It chooses the port with the:

1. **Lowest Path Cost** to the Root Bridge
    
2. If tie → **Lowest BID (Bridge ID)** from the neighbor switch
    
3. If tie → **Lowest port ID** (lowest port number of the neighbor)
    

📌 **Path Cost** is calculated based on the **port speed**:

|Port Speed|STP Cost|
|---|---|
|10 Mbps|100|
|100 Mbps|19|
|1 Gbps|4|
|10 Gbps|2|

🔁 This Root Port will **forward traffic toward the Root Bridge**.

---
### **Step 3: Select Designated Ports (DP)**

- On each **segment (collision domain)**, the switch with the **lowest cost to Root** becomes **Designated Switch**.
    
- The port on that switch is the **Designated Port** (used for forwarding).
    

🧠 Rule: Only **one Designated Port per segment**.

---

### **Step 4: Block Redundant Ports**

- Any port that is **not** a **Root Port or Designated Port** is placed in the **Blocking state** to avoid loops.
## ⚙️ Types of STP:

|Type|Description|
|---|---|
|**STP**|Original 802.1D (slow ~50 sec)|
|**RSTP**|Rapid STP (802.1w) — faster (~5 sec)|
|**MSTP**|Multiple STP (802.1s) — for VLANs|
|**PVST+**|Cisco’s version — one STP per VLAN|
|**RPVST+**|Cisco’s rapid version per VLAN|
## ==🧠 What is DNS?==

**DNS (Domain Name System)** It translates human-readable domain names (like `www.google.com`) into IP addresses (like `142.250.195.68`) that computers use to communicate.

---
## ⚙️ Step-by-Step DNS Resolution Process:

Let's say you want to visit `www.example.com`.

---
### **1. Browser Cache Check**

First, your browser checks if it already knows the IP address from past requests (browser DNS cache).

If **not found**, it goes to the next step.

---
### **2. OS Resolver Cache Check**

The Operating System checks its own DNS cache.

If **not found**, it asks the **DNS Resolver** (typically your ISP's DNS server).

---

### **3. Recursive Resolver (DNS Resolver)**

The DNS Resolver begins querying other DNS servers **recursively** to resolve the domain. Here's how:

---
### **4. Query Root Name Server**

The resolver asks a **Root Name Server**:  
_"Hey, do you know where to find `example.com`?"_

➡️ **Root servers don't know the IP**, but they know where to find the **Top Level Domain (TLD)** name servers (e.g., `.com`).

So, it replies:  
_"Ask the `.com` TLD server."_

---
### **5. Query TLD Name Server**

The resolver now asks the **`.com` TLD Name Server**:  
_"Hey, do you know where `example.com` is?"_

➡️ It replies with a referral to the **Authoritative Name Server** (NS record) for `example.com`.

---
### ✅ **6. Authoritative Name Server

This is where the **NS record** is important!

The **Authoritative Name Server** is the actual server that has the **final answer** for `example.com`.

It replies with the **A record** (IPv4 address) or **AAAA record** (IPv6 address) for `www.example.com`.

Example:

`A record → www.example.com → 93.184.216.34`

---
### **7. Return to Client**

The DNS Resolver now sends this IP back to your system, and your browser can now connect to the web server at that IP.

### ==🔥 **What is a Firewall (in detail)?**==

A **firewall** is a **security system** (hardware or software) that **monitors and controls incoming and outgoing network traffic** based on **predefined security rules**.
#### 🔐 Purpose:

To **prevent unauthorized access** to or from a **private network**. Firewalls act as a **barrier** between a trusted internal network and untrusted external networks (like the internet).

#### 🧱 Types of Firewalls:

1. **Packet Filtering Firewall** – Checks packets against rules (IP, port, protocol).
    
2. **Stateful Inspection Firewall** – Tracks connection states.
    
3. **Proxy Firewall** – Works at the application layer and acts as a middleman.
    
4. **Next-Gen Firewall (NGFW)** – Deep packet inspection, application awareness, intrusion prevention, etc.
---
### 🏰 What is a DMZ (Demilitarized Zone)?

A **DMZ** is a **separate network** that adds an **extra layer of security** between the **public internet** and the **internal (private) network**.

#### 🧩 Why Use DMZ?

To **host public-facing services** like:

- Web servers
    
- Email servers
    
- DNS servers
    
- FTP servers
These services are exposed to the internet but **isolated** from the internal LAN. If a hacker compromises a DMZ system, they **still can't access the internal network directly**.

---
### ❓ So, Is DMZ a Physical Thing?

It **can be both**:
#### 1. **Physical DMZ:**

- Using **a separate physical firewall interface** connected to a DMZ switch.
    
- This setup **physically separates** the DMZ network.
#### 2. **Logical DMZ (more common today):**

- Created **virtually inside a firewall** using **VLANs** and **rules**.
    
- No need for separate hardware—firewall creates zones logically.

# ==What is the purpose of an IDS and IPS?==
### 🔍 **IDS (Intrusion Detection System)**

- **Purpose**: Monitors network traffic and alerts the administrator if suspicious or malicious activity is detected.
    
- **Action**: _Detects only_. It does **not block** traffic.
    
- **Placement**: Usually placed _outside_ the firewall or _inside_ the network to monitor internal traffic.
    
- **Example**: Alerts you if someone is scanning your network or trying SQL injection.
#### Types of IDS:

- **NIDS (Network-based IDS)** – Monitors traffic on a network.
    
- **HIDS (Host-based IDS)** – Installed on individual devices to monitor system behavior.
---
### 🛡️ **IPS (Intrusion Prevention System)**

- **Purpose**: Monitors and actively **blocks or prevents** malicious traffic.
    
- **Action**: _Detects and blocks_ traffic in real-time.
    
- **Placement**: _Inline_, between the network and the device or firewall.
#### Example:

- Automatically blocks IPs that are performing port scans or drops packets matching attack signatures.
---
### 🔁 **IDS vs IPS**

|Feature|IDS|IPS|
|---|---|---|
|Primary Role|Detection|Prevention|
|Action Taken|Alerts admin only|Blocks malicious traffic|
|Placement|Out-of-band (sniffer mode)|Inline (in path of traffic)|
|Latency|None (passive)|May introduce slight latency|
