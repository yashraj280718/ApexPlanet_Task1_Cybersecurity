# OSI Model

This document provides a comprehensive overview of the **OSI (Open Systems Interconnection) Model**, its seven layers, and real-world examples for each layer. Use this as part of your Task 1 documentation for networking fundamentals.

---

## Overview

The OSI Model is a conceptual framework used to understand network interactions in seven distinct layers. Each layer serves a specific function and communicates with the layers directly above and below it.

| Layer Number | Layer Name          | Primary Function                                   |
|--------------|---------------------|----------------------------------------------------|
| 7            | Application         | Network services to end-user applications          |
| 6            | Presentation        | Data translation, encryption, and compression      |
| 5            | Session             | Managing and controlling communication sessions    |
| 4            | Transport           | Reliable data transfer and flow control            |
| 3            | Network             | Logical addressing and routing                     |
| 2            | Data Link           | Node-to-node data transfer and error detection     |
| 1            | Physical            | Transmission of raw bit streams over physical media|

---

<img width="1800" height="1798" alt="Image" src="https://github.com/user-attachments/assets/44f7aa0a-8178-4c32-a00e-4dbd88800300" />

---
## 1. Layer 7: Application Layer

- **Purpose:** Provides network services directly to user applications.
- **Key Responsibilities:** Resource sharing, remote file access, email, web browsing.
- **Common Protocols:** HTTP, HTTPS, FTP, SMTP, DNS, Telnet.
- **Examples:**
  - Web browsers (Chrome, Firefox) using HTTP/HTTPS.
  - Email clients (Outlook, Thunderbird) using SMTP/IMAP/POP3.
  - DNS resolution via domain lookup.

<img width="318" height="159" alt="Image" src="https://github.com/user-attachments/assets/51920075-1022-4804-a9b7-cecfd2425eae" />

---

## 2. Layer 6: Presentation Layer

- **Purpose:** Translates data between application and network formats.
- **Key Responsibilities:** Data encryption/decryption, compression/decompression, character encoding (ASCII, EBCDIC).
- **Examples:**
  - SSL/TLS encryption for HTTPS connections.
  - JPEG, GIF image compression.
  - Data serialization formats like JSON, XML.

<img width="317" height="159" alt="Image" src="https://github.com/user-attachments/assets/8a24cb55-9c54-44b0-8a00-1a3480faa924" />

---

## 3. Layer 5: Session Layer

- **Purpose:** Manages sessions or connections between applications.
- **Key Responsibilities:** Establishing, maintaining, and terminating communication sessions; synchronization.
- **Examples:**
  - TCP session management (establishing and tearing down connections).
  - NetBIOS sessions in Windows networks.
  - SSH session management.

![Image](https://github.com/user-attachments/assets/ffcc3418-5e7b-4580-8be7-874c20c11188))

---

## 4. Layer 4: Transport Layer

- **Purpose:** Ensures reliable data transfer between hosts.
- **Key Responsibilities:** Segmentation, error detection and correction, flow control, and end-to-end communication.
- **Protocols:** TCP (connection-oriented, reliable), UDP (connectionless, low overhead).
- **Examples:**
  - TCP three-way handshake (SYN, SYN-ACK, ACK).
  - UDP streaming for VoIP and video conferencing.
  - Retransmission of lost segments in FTP transfers.

<img width="354" height="142" alt="Image" src="https://github.com/user-attachments/assets/5b3b01f1-c196-4107-8873-a43206fc55e1" />

---

## 5. Layer 3: Network Layer

- **Purpose:** Determines how data is transferred between networks and routed to the destination.
- **Key Responsibilities:** Logical addressing (IP), routing, packet forwarding, fragmentation.
- **Protocols:** IP, ICMP, OSPF, BGP.
- **Examples:**
  - IPv4 and IPv6 addressing and routing.
  - ICMP ping and traceroute utilities.
  - Dynamic routing protocols in routers (OSPF, BGP).

<img width="320" height="157" alt="Image" src="https://github.com/user-attachments/assets/72c5cc55-f0ae-4508-ae95-1547e75048f4" />

---

## 6. Layer 2: Data Link Layer

- **Purpose:** Provides node-to-node data transfer and handles error detection from the physical layer.
- **Key Responsibilities:** Framing, MAC addressing, error detection (CRC), flow control.
- **Sublayers:** Logical Link Control (LLC), Media Access Control (MAC).
- **Examples:**
  - Ethernet frame structure and MAC addressing.
  - Switch operations using MAC address tables.
  - PPP and HDLC in WAN connections.

<img width="399" height="126" alt="Image" src="https://github.com/user-attachments/assets/9875bf78-9d80-4ee4-a9cc-bee698a9e4a1" />

<img width="300" height="168" alt="Image" src="https://github.com/user-attachments/assets/cca8d47e-dab4-4bbc-859f-5bbe4683ffa6" />

---

## 7. Layer 1: Physical Layer

- **Purpose:** Transmits raw bits over physical medium.
- **Key Responsibilities:** Electrical, optical, or radio frequency signaling, bit rate control, physical topology.
- **Examples:**
  - Ethernet cables (Cat5e, Cat6) and connectors (RJ45).
  - Fiber optic transmission.
  - Wireless transmission (Wi-Fi, Bluetooth) radio frequencies.

<img width="259" height="194" alt="Image" src="https://github.com/user-attachments/assets/2f58cb53-8279-46fb-b1e6-f1a0947a1a41" />

---

## Practical Examples

1. **Web Browsing (HTTP over TCP/IP):** Data enters at Application Layer (HTTP), encrypted at Presentation Layer (TLS), session managed at Session Layer, segmented and reliable transfer at Transport Layer (TCP), routing via Network Layer (IP), framed at Data Link Layer (Ethernet), and transmitted over cables via Physical Layer.

2. **VoIP Call (UDP Streaming):** Voice encoded at Presentation Layer, session set up at Session Layer (SIP), transported via UDP at Transport Layer, routing through IP at Network Layer, MAC-based switching at Data Link Layer, and sent over wireless medium at Physical Layer.

3. **File Transfer (FTP):** FTP client initiates transfer at Application Layer, sessions at Session Layer, uses TCP at Transport Layer for reliability, IP routing, Ethernet framing, and physical transmission via cables.
