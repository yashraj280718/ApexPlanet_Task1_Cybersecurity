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

## 1. Layer 7: Application Layer

- **Purpose:** Provides network services directly to user applications.
- **Key Responsibilities:** Resource sharing, remote file access, email, web browsing.
- **Common Protocols:** HTTP, HTTPS, FTP, SMTP, DNS, Telnet.
- **Examples:**
  - Web browsers (Chrome, Firefox) using HTTP/HTTPS.
  - Email clients (Outlook, Thunderbird) using SMTP/IMAP/POP3.
  - DNS resolution via domain lookup.

---

## 2. Layer 6: Presentation Layer

- **Purpose:** Translates data between application and network formats.
- **Key Responsibilities:** Data encryption/decryption, compression/decompression, character encoding (ASCII, EBCDIC).
- **Examples:**
  - SSL/TLS encryption for HTTPS connections.
  - JPEG, GIF image compression.
  - Data serialization formats like JSON, XML.

---

## 3. Layer 5: Session Layer

- **Purpose:** Manages sessions or connections between applications.
- **Key Responsibilities:** Establishing, maintaining, and terminating communication sessions; synchronization.
- **Examples:**
  - TCP session management (establishing and tearing down connections).
  - NetBIOS sessions in Windows networks.
  - SSH session management.

---

## 4. Layer 4: Transport Layer

- **Purpose:** Ensures reliable data transfer between hosts.
- **Key Responsibilities:** Segmentation, error detection and correction, flow control, and end-to-end communication.
- **Protocols:** TCP (connection-oriented, reliable), UDP (connectionless, low overhead).
- **Examples:**
  - TCP three-way handshake (SYN, SYN-ACK, ACK).
  - UDP streaming for VoIP and video conferencing.
  - Retransmission of lost segments in FTP transfers.

---

## 5. Layer 3: Network Layer

- **Purpose:** Determines how data is transferred between networks and routed to the destination.
- **Key Responsibilities:** Logical addressing (IP), routing, packet forwarding, fragmentation.
- **Protocols:** IP, ICMP, OSPF, BGP.
- **Examples:**
  - IPv4 and IPv6 addressing and routing.
  - ICMP ping and traceroute utilities.
  - Dynamic routing protocols in routers (OSPF, BGP).

---

## 6. Layer 2: Data Link Layer

- **Purpose:** Provides node-to-node data transfer and handles error detection from the physical layer.
- **Key Responsibilities:** Framing, MAC addressing, error detection (CRC), flow control.
- **Sublayers:** Logical Link Control (LLC), Media Access Control (MAC).
- **Examples:**
  - Ethernet frame structure and MAC addressing.
  - Switch operations using MAC address tables.
  - PPP and HDLC in WAN connections.

---

## 7. Layer 1: Physical Layer

- **Purpose:** Transmits raw bits over physical medium.
- **Key Responsibilities:** Electrical, optical, or radio frequency signaling, bit rate control, physical topology.
- **Examples:**
  - Ethernet cables (Cat5e, Cat6) and connectors (RJ45).
  - Fiber optic transmission.
  - Wireless transmission (Wi-Fi, Bluetooth) radio frequencies.

---

## Practical Examples

1. **Web Browsing (HTTP over TCP/IP):** Data enters at Application Layer (HTTP), encrypted at Presentation Layer (TLS), session managed at Session Layer, segmented and reliable transfer at Transport Layer (TCP), routing via Network Layer (IP), framed at Data Link Layer (Ethernet), and transmitted over cables via Physical Layer.

2. **VoIP Call (UDP Streaming):** Voice encoded at Presentation Layer, session set up at Session Layer (SIP), transported via UDP at Transport Layer, routing through IP at Network Layer, MAC-based switching at Data Link Layer, and sent over wireless medium at Physical Layer.

3. **File Transfer (FTP):** FTP client initiates transfer at Application Layer, sessions at Session Layer, uses TCP at Transport Layer for reliability, IP routing, Ethernet framing, and physical transmission via cables.
