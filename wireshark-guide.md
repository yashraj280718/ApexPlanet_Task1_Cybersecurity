# Wireshark - Packet Analysis Guide

A comprehensive guide to using Wireshark for network traffic analysis and troubleshooting as part of Task 1 (ApexPlanet Cybersecurity Internship).

---

## What is Wireshark?

Wireshark is a widely-used open-source network protocol analyzer that allows you to capture and interactively browse network traffic in real-time. It provides deep inspection of hundreds of protocols and is essential for:

- Network troubleshooting and diagnostics
- Protocol development and analysis
- Security analysis and penetration testing
- Learning network protocols and communication
- Detecting malicious network activity

Wireshark can decode various protocols, display packet contents in human-readable format, and help identify network issues or security threats.

---

## Installation

### On Kali Linux / Ubuntu / Debian

1. Update your package list:
```bash
sudo apt update
```

2. Install Wireshark:
```bash
sudo apt install wireshark
```

3. During installation, you'll be asked: **"Should non-superusers be able to capture packets?"**
   - Select **Yes** to allow non-root users to capture traffic

4. Add your user to the Wireshark group:
```bash
sudo usermod -aG wireshark $(whoami)
```

5. Log out and log back in (or reboot) for group changes to take effect

6. Launch Wireshark:
```bash
wireshark
```
Or find it in Applications → Sniffing & Spoofing → Wireshark

<img width="1677" height="815" alt="image" src="https://github.com/user-attachments/assets/313f2c14-66e5-4fd1-88dd-08a2bd72326a" />

---

## Basic Usage

### 1. Select Network Interface

When you launch Wireshark, you'll see a list of available network interfaces:

- **eth0** - Wired Ethernet connection
- **wlan0** - Wireless network interface
- **lo** - Loopback interface (localhost traffic)
- **any** - Capture on all interfaces

**Tip:** Choose the interface where you expect the traffic you want to analyze.

### 2. Start Capture

- Click the **blue shark fin icon** (Start Capturing Packets) in the toolbar
- Or press **Ctrl + E**
- Or go to **Capture → Start**

Wireshark will immediately begin capturing all packets on the selected interface.

<img width="1919" height="879" alt="image" src="https://github.com/user-attachments/assets/76826f89-4bd8-4274-8bab-eccf53abcf2c" />

### 3. Apply Filters

Use the **Display Filter** bar (located below the toolbar) to filter captured traffic:

- Type your filter expression
- Press **Enter** or click the **arrow button** to apply
- Click the **X button** to clear the filter

### 4. Analyze Packets

Wireshark displays three panes:

- **Packet List Pane (Top):** Shows all captured packets with summary information
- **Packet Details Pane (Middle):** Displays protocol layers and headers of the selected packet
- **Packet Bytes Pane (Bottom):** Shows the raw hexadecimal and ASCII data

### 5. Stop Capture

- Click the **red square icon** (Stop Capturing Packets)
- Or press **Ctrl + E** again
- Or go to **Capture → Stop**

---

## Common Display Filters

Display filters allow you to focus on specific traffic after capturing packets.

### Basic Protocol Filters

| Filter | Description |
|--------|-------------|
| `http` | Show only HTTP traffic |
| `https` | Show only HTTPS traffic |
| `dns` | Show only DNS queries and responses |
| `tcp` | Show only TCP packets |
| `udp` | Show only UDP packets |
| `icmp` | Show only ICMP packets (ping) |
| `arp` | Show only ARP packets |
| `ssh` | Show only SSH traffic |
| `ftp` | Show only FTP traffic |
| `smtp` | Show only email (SMTP) traffic |

### IP Address Filters

| Filter | Description |
|--------|-------------|
| `ip.addr == 192.168.1.1` | Show traffic to/from specific IP |
| `ip.src == 192.168.1.1` | Show traffic from specific source IP |
| `ip.dst == 192.168.1.1` | Show traffic to specific destination IP |
| `ip.addr == 192.168.1.0/24` | Show traffic to/from entire subnet |
| `!(ip.addr == 192.168.1.1)` | Exclude specific IP address |

### Port Filters

| Filter | Description |
|--------|-------------|
| `tcp.port == 80` | Show traffic on TCP port 80 (HTTP) |
| `tcp.port == 443` | Show traffic on TCP port 443 (HTTPS) |
| `tcp.srcport == 80` | Show traffic from source port 80 |
| `tcp.dstport == 80` | Show traffic to destination port 80 |
| `udp.port == 53` | Show traffic on UDP port 53 (DNS) |

### Logical Operators

| Operator | Description | Example |
|----------|-------------|---------|
| `and` or `&&` | Both conditions must be true | `ip.src == 192.168.1.1 and tcp.port == 80` |
| `or` or `||` | Either condition can be true | `tcp.port == 80 or tcp.port == 443` |
| `not` or `!` | Negates the condition | `not arp` |

### Comparison Operators

| Operator | Description | Example |
|----------|-------------|---------|
| `==` | Equal to | `ip.addr == 192.168.1.1` |
| `!=` | Not equal to | `tcp.port != 80` |
| `>` | Greater than | `frame.len > 1000` |
| `<` | Less than | `frame.len < 100` |
| `>=` | Greater than or equal | `tcp.window_size >= 65535` |
| `<=` | Less than or equal | `ip.ttl <= 64` |

---

## Advanced Filtering Examples

### HTTP Analysis

```
http.request.method == "GET"              # Show only HTTP GET requests
http.request.method == "POST"             # Show only HTTP POST requests
http.response.code == 200                 # Show HTTP 200 OK responses
http.response.code == 404                 # Show HTTP 404 Not Found errors
http.host contains "example.com"          # Show requests to specific domain
```

### TCP Analysis

```
tcp.flags.syn == 1                        # Show TCP SYN packets (connection attempts)
tcp.flags.reset == 1                      # Show TCP reset packets
tcp.analysis.retransmission               # Show retransmitted packets
tcp.analysis.duplicate_ack                # Show duplicate acknowledgments
```

### Combined Filters

```
ip.src == 192.168.1.100 and http          # HTTP traffic from specific IP
tcp.port == 80 and ip.addr == 10.0.0.5    # Port 80 traffic to/from specific IP
dns and ip.dst == 8.8.8.8                 # DNS queries to Google DNS
!(arp or icmp or dns)                     # Exclude ARP, ICMP, and DNS
```

---

## Useful Features

### Follow TCP Stream

1. Right-click on any TCP packet
2. Select **Follow → TCP Stream**
3. View the entire conversation in a readable format

This is extremely useful for reading HTTP requests/responses, FTP commands, or any text-based protocol.

### Packet Statistics

- **Statistics → Protocol Hierarchy** - Shows breakdown of protocols in capture
- **Statistics → Conversations** - Shows all conversations (connections) between hosts
- **Statistics → Endpoints** - Lists all IP addresses and their traffic volume
- **Statistics → I/O Graph** - Visual graph of traffic over time

### Coloring Rules

Wireshark uses colors to help identify different types of traffic:

- **Light purple** - TCP traffic
- **Light blue** - UDP traffic
- **Black** - Packets with errors
- **Green** - HTTP traffic
- **Light green** - DNS traffic
- **Yellow** - Routing protocols

You can customize colors via **View → Coloring Rules**.

### Export Objects

Extract files transferred over HTTP, SMB, or other protocols:

1. Go to **File → Export Objects**
2. Choose protocol (HTTP, SMB, TFTP, etc.)
3. Select files to save

---

## Capture Filters vs Display Filters

### Capture Filters

- Applied **before** packets are captured
- Reduces capture file size
- Uses BPF (Berkeley Packet Filter) syntax
- Set in the capture options **before** starting capture

**Examples:**
```
host 10.10.169.194                        # Capture traffic to/from specific host
port 80                                   # Capture only port 80 traffic
tcp                                       # Capture only TCP packets
not broadcast and not multicast           # Exclude broadcast/multicast traffic
```

### Display Filters

- Applied **after** packets are captured
- Does not reduce capture file size
- More powerful and flexible than capture filters
- Can be changed anytime during or after capture

**Use display filters when you want to analyze specific traffic from a complete capture.**

---

## Practical Examples for Cybersecurity

### Detect Port Scanning

```
tcp.flags.syn == 1 and tcp.flags.ack == 0
```
Shows TCP SYN packets without ACK - common in port scans.

### Find Failed Login Attempts

```
ftp.response.code == 530                  # FTP failed logins
ssh.message.code == 51                    # SSH authentication failures
```

### Identify Suspicious DNS Queries

```
dns.qry.name contains "malware"
dns.qry.name contains "phishing"
```

### Monitor Outbound Connections

```
ip.src == 192.168.1.0/24 and not ip.dst == 192.168.1.0/24
```
Shows traffic leaving your local network.

---

## Saving and Loading Captures

### Save Capture

1. **File → Save As**
2. Choose format:
   - **.pcapng** (recommended - Wireshark native format)
   - **.pcap** (standard format compatible with other tools)
3. Save to desired location

### Load Existing Capture

1. **File → Open**
2. Select **.pcap** or **.pcapng** file
3. Analyze offline without capturing live traffic

---

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl + E` | Start/Stop capture |
| `Ctrl + K` | Open capture options |
| `Ctrl + O` | Open file |
| `Ctrl + S` | Save capture |
| `Ctrl + F` | Find packet |
| `Ctrl + G` | Go to packet number |
| `Ctrl + /` | Apply display filter |
| `Alt + →` | Next packet |
| `Alt + ←` | Previous packet |

---

## Tips for Effective Analysis

1. **Start with a clean capture** - Stop unnecessary services before capturing
2. **Use filters liberally** - Don't try to analyze everything at once
3. **Follow streams** - Reconstruct full conversations for context
4. **Check statistics** - Get an overview before diving into individual packets
5. **Save your work** - Always save important captures for documentation
6. **Learn protocols** - Understanding how protocols work helps you analyze traffic
7. **Practice regularly** - The more you use Wireshark, the more proficient you become

---

## Common Issues and Solutions

### "Permission denied" Error

**Solution:** Add user to wireshark group and reboot:
```bash
sudo usermod -aG wireshark $(whoami)
sudo reboot
```

### No Interfaces Listed

**Solution:** Run Wireshark with sudo (not recommended for security):
```bash
sudo wireshark
```

Or fix permissions permanently with:
```bash
sudo setcap cap_net_raw,cap_net_admin+eip /usr/bin/dumpcap
```

### Capture Shows No Traffic

- Verify you selected the correct interface
- Check if the interface is connected to the network
- Disable VPN if active (may redirect traffic)

---

## Resources

- **Official Documentation:** [https://www.wireshark.org/docs/](https://www.wireshark.org/docs/)
- **Display Filter Reference:** [https://www.wireshark.org/docs/dfref/](https://www.wireshark.org/docs/dfref/)
- **Sample Captures:** [https://wiki.wireshark.org/SampleCaptures](https://wiki.wireshark.org/SampleCaptures)
- **Wireshark User Guide:** [https://www.wireshark.org/docs/wsug_html_chunked/](https://www.wireshark.org/docs/wsug_html_chunked/)

---

**Practice Exercise:** Capture your own network traffic, apply filters, and identify different types of protocols in use.

*Guide prepared for Task 1 - Tools Familiarization (ApexPlanet Cybersecurity Internship)*
