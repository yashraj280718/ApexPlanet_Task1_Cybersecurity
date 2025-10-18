

# **ApexPlanet Cybersecurity & Ethical Hacking Internship**  
## **Task 1: Foundations of Cybersecurity (Days 1–12)**  

**Intern:** Yashraj Giri Goswami
**Organization:** ApexPlanet Software Pvt. Ltd.  
**Duration:** 1 Sept, 2025 – 29 Oct, 2025

---

# Table of Contents

1. [Lab Environment Setup Guide](#lab-environment-setup-guide)
2. [Linux Commands Cheat Sheet](#linux-commands-cheat-sheet)
3. [OSI Model - Complete Notes](#osi-model---complete-notes)
4. [Symmetric Encryption Demo Script](#symmetric-encryption-demo-script)
5. [Wireshark - Packet Analysis Guide](#wireshark---packet-analysis-guide)
6. [Learning Outcomes](#learning-outcomes)

---

# 1. Lab Environment Setup Guide

# Prerequisites
- **Computer Requirements:-**
  - Minimum 8GB RAM (16GB recommended for smooth performance)
  - At least 80GB free disk space
  - 64-bit processor with virtualization support
- **Virtualization enabled in BIOS/UEFI**
- **VMware Workstation Pro** (Free for personal use as of 2025)

***

# Step 0: Enable Virtualization in BIOS

Before installing VMware, ensure hardware virtualization is enabled in your system BIOS/UEFI.

### For Windows 11/10:

**Method 1: Check if Virtualization is Already Enabled**

1. Press `Ctrl + Shift + Esc` to open Task Manager
2. Click on the **Performance** tab
3. Select **CPU** from the left panel
4. Look for **Virtualization** at the bottom right
5. If it shows "Enabled", you can skip to Step 1

**Method 2: Enable Virtualization in BIOS**

1. **Restart your computer**
2. **Enter BIOS Setup** - Press the appropriate key during boot:
   - **Dell**: F2 or F12
   - **HP**: F10 or Esc
   - **Lenovo**: F1 or F2
   - **ASUS**: F2 or Del
   - **Acer**: F2 or Del[3][4]

3. **Navigate to Virtualization Settings**:
   - Look for settings named:
     - **Intel VT-x** (Intel processors)
     - **AMD-V** (AMD processors)
     - **Virtualization Technology**
     - **VT-d**
     - **SVM Mode**[4][5][3]

4. **Enable the setting** by changing it to **Enabled**
5. **Save and Exit** (usually F10)
6. **Restart your computer**

**Screenshot Reference:** `screenshots/bios-virtualization-enabled.png`

***

# Step 1: Install VMware Workstation Pro

### Download VMware Workstation Pro

1. Visit the official VMware website:
   ```
   https://www.vmware.com/products/desktop-hypervisor/workstation-and-fusion
   ```

2. Click on **"Download Now"** for VMware Workstation Pro

3. **Accept the terms and conditions**[6]

4. The installer file (approximately 600-700 MB) will download as:
   - **Windows**: `VMware-workstation-full-xx.x.x-xxxxxxx.exe`
   - **Linux**: `VMware-Workstation-Full-xx.x.x-xxxxxxx.bundle`

**Screenshot Reference:** `screenshots/vmware-download-page.png`

***

### Install VMware Workstation Pro on Windows

1. **Locate the downloaded installer** in your Downloads folder

2. **Right-click** the installer file (`VMware-workstation-full-xx.x.x-xxxxxxx.exe`)

3. Select **"Run as administrator"**

4. Click **"Yes"** when prompted by User Account Control (UAC)

5. **Installation Wizard Steps:**

   **a. Welcome Screen**
   - Click **Next**

   **b. License Agreement**
   - Read and accept the End-User License Agreement
   - Check **"I accept the terms in the License Agreement"**
   - Click **Next**

   **c. Installation Directory**
   - Keep the default installation path or click **Change** to select a custom location:
     ```
     Default: C:\Program Files (x86)\VMware\VMware Workstation\
     ```
   - Click **Next**

   **d. User Experience Settings**
   - **Enhanced Keyboard Driver**: ✓ (Recommended - improves keyboard handling in VMs)
   - **Check for product updates on startup**: ✓ (Optional)
   - **Join VMware Customer Experience Improvement Program**: (Optional)
   - Click **Next**

   **e. Shortcuts**
   - ✓ Desktop
   - ✓ Start Menu Programs folder
   - Click **Next**

   **f. Ready to Install**
   - Review your settings
   - Click **Install**

6. **Wait for Installation** (usually 3-5 minutes)

7. **Installation Complete**
   - Click **Finish**
   - You may need to **restart your computer**

**Screenshot Reference:** `screenshots/vmware-installation-complete.png`

***

### First Launch and License Activation

1. **Launch VMware Workstation Pro** from:
   - Desktop shortcut, or
   - Start Menu → VMware Workstation Pro

2. **License Options:**
   - **For Personal Use**: Select "Use VMware Workstation Pro for Personal Use" (Free as of 2025)[6][1]
   - **For Commercial Use**: Enter your license key
   - Click **Continue**

3. VMware Workstation Pro is now ready to use

**Screenshot Reference:** `screenshots/vmware-first-launch.png`

***

# Step 2: Install Kali Linux

### Download Kali Linux ISO

1. Visit the official Kali Linux download page:
   ```
   https://www.kali.org/get-kali/
   ```

2. Select **"Installer Images"**

3. Download the **64-bit Installer ISO**:
   - File name: `kali-linux-202X.X-installer-amd64.iso`
   - Size: Approximately 3-4 GB


### Create Kali Linux Virtual Machine

1. **Open VMware Workstation Pro**

2. Click **"Create a New Virtual Machine"**

3. **Configuration Type:**
   - Select **"Custom (advanced)"** for more control
   - Click **Next**

4. **Hardware Compatibility:**
   - Select **"Workstation 17.x"** (or latest available)
   - Click **Next**

5. **Install Operating System:**
   - Select **"Installer disc image file (iso)"**
   - Click **Browse**
   - Navigate to the downloaded Kali Linux ISO file
   - Select the ISO file
   - Click **Next**

**Screenshot Reference:** `screenshots/kali-vm-iso-selection.png`

6. **Guest Operating System:**
   - Select **"Linux"**
   - Version: **"Debian 12.x 64-bit"** (Kali is Debian-based)
   - Click **Next**

7. **Virtual Machine Name and Location:**
   - Name: `Kali Linux 2025`
   - Location: Choose where to store VM files (default is fine)
     ```
     Default: C:\Users\[YourName]\Documents\Virtual Machines\Kali Linux 2025\
     ```
   - Click **Next**

8. **Processor Configuration:**
   - Number of processors: **minimum 1**
   - Number of cores per processor: **2** (or 4 if you have 8+ cores)
   - Click **Next**

9. **Memory Allocation:**
   - Recommended: **2048 MB (2 GB)** minimum
   - Better performance: **4096 MB (4 GB)**
   - Click **Next**

10. **Network Type:**
    - Select **"Use network address translation (NAT)"** (for now, we'll change this later)
    - Click **Next**

11. **I/O Controller Types:**
    - Select **"LSI Logic (Recommended)"**
    - Click **Next**

12. **Virtual Disk Type:**
    - Select **"SCSI (Recommended)"**
    - Click **Next**

13. **Disk:**
    - Select **"Create a new virtual disk"**
    - Click **Next**

14. **Disk Size:**
    - Maximum disk size: **80 GB** (recommended)
    - Select **"Store virtual disk as a single file"**
    - Click **Next**

15. **Disk File:**
    - Accept default filename
    - Click **Next**

16. **Ready to Create:**
    - Review VM settings
    - Click **"Customize Hardware"** to make any final adjustments (optional)
    - Click **Finish**

**Screenshot Reference:** `screenshots/kali-vm-created.png`

***

### Install Kali Linux Operating System

1. **Power on the Virtual Machine** by clicking **"Power on this virtual machine"**

2. **Kali Linux Boot Menu** will appear:
   - Select **"Graphical Install"** (recommended)
   - Press **Enter**

**Screenshot Reference:** `screenshots/kali-boot-menu.png`

3. **Language Selection:**
   - Select your preferred language (e.g., **English**)
   - Click **Continue**

4. **Location:**
   - Select your country/region
   - Click **Continue**

5. **Keyboard Configuration:**
   - Select your keyboard layout
   - Click **Continue**

6. **Network Configuration:**
   - Hostname: Enter a name (e.g., `kali-lab`)
   - Click **Continue**

7. **Domain Name:**
   - Leave blank or enter a domain (e.g., `local`)
   - Click **Continue**

8. **User Account Setup:**
   - Full name: Your name
   - Username: `kali` (recommended)
   - Password: Create a strong password
   - Re-enter password
   - Click **Continue**

9. **Partition Disks:**
   - Select **"Guided - use entire disk"**
   - Click **Continue**
   - Select the virtual disk
   - Select **"All files in one partition"**
   - Select **"Finish partitioning and write changes to disk"**
   - Confirm: **Yes**
   - Click **Continue**

10. **Software Selection:**
    - Default selection includes: 
      - ✓ Kali Desktop Environment (Xfce)
      - ✓ Top 10 security tools
    - You can select **"Kali Large"** for more tools (requires more disk space)
    - Click **Continue**

11. **Install GRUB Boot Loader:**
    - Select **Yes** to install GRUB
    - Select the virtual disk (`/dev/sda`)
    - Click **Continue**

12. **Installation Complete:**
    - Click **Continue** to reboot
    - VM will restart automatically

13. **Login to Kali Linux:**
    - Username: `username you created`
    - Password: Your password
    - Press **Enter**

**Screenshot Reference:** `screenshots/kali-desktop.png`

***

### Update Kali Linux

After first login, open terminal and run:

```bash
sudo apt update && sudo apt upgrade -y
sudo apt dist-upgrade -y
```

**Screenshot Reference:** `screenshots/kali-system-update.png`

***

## Step 3: Setup Metasploitable2

### Download Metasploitable2

1. Visit the official Metasploitable2 download page:
   ```
   https://sourceforge.net/projects/metasploitable/files/Metasploitable2/
   ```

2. Download **`metasploitable-linux-2.0.0.zip`**
   - Size: Approximately 825 MB

3. **Extract the ZIP file** to a location on your computer:
   - Right-click the ZIP file
   - Select **"Extract All"** or use 7-Zip/WinRAR
   - Choose destination folder (e.g., `C:\Virtual Machines\Metasploitable2\`)

**Screenshot Reference:** `screenshots/metasploitable2-extracted-files.png`

***

### Import Metasploitable2 into VMware

1. **Open VMware Workstation Pro**

2. Click **File → Open**

3. Navigate to the extracted Metasploitable2 folder

4. Select the file: **`Metasploitable.vmx`**

5. Click **Open**

6. Metasploitable2 VM will appear in your VM library

**Screenshot Reference:** `screenshots/metasploitable2-imported.png`

***

### Configure Metasploitable2 Settings

1. **Right-click** on Metasploitable2 VM

2. Select **"Settings"**

3. **Memory:**
   - Recommended: **512 MB** (default is fine)

4. **Network Adapter:**
   - **Important**: Change from NAT to **"Host-only"** (we'll configure this in Step 4)
   - Click **OK**

**Screenshot Reference:** `screenshots/metasploitable2-settings.png`

***

### Start Metasploitable2

1. **Select** Metasploitable2 VM

2. Click **"Power on this virtual machine"**

3. If prompted with **"I copied it"** or **"I moved it"**, select **"I copied it"**

4. **Login Screen** will appear:
   - **Username**: `msfadmin`
   - **Password**: `msfadmin`

5. **Verify Installation** by checking IP address:
   ```bash
   ifconfig
   ```
   You should see network interface details with an IP address

**Screenshot Reference:** `screenshots/metasploitable2-login.png`

***

# Step 4: Network Configuration (Host-Only Adapter)

Creating a Host-Only network ensures your penetration testing lab is **isolated from the internet** and external networks, preventing accidental attacks on production systems.

### Create Host-Only Network in VMware

1. **Open VMware Workstation Pro**

2. Go to **Edit → Virtual Network Editor**

3. Click **"Change Settings"** (requires administrator privileges)

4. Click **"Add Network"**

5. Select an available network (e.g., **VMnet2** or **VMnet3**)

6. Click **OK**

7. **Configure the Host-Only Network:**
   - Network Name: **VMnet2** (or your chosen network)
   - Type: Select **"Host-only"**
   - ✓ **Connect a host virtual adapter to this network**
   - Subnet IP: **192.168.100.0**
   - Subnet mask: **255.255.255.0**

8. **DHCP Settings** (Optional):
   - Click **"DHCP Settings"**
   - Enable DHCP if you want automatic IP assignment
   - Or disable for manual configuration

9. Click **OK** to save

10. Click **Apply**

11. Click **OK** to close Virtual Network Editor

**Screenshot Reference:** `screenshots/vmware-hostonly-network.png`

***

### Configure Kali Linux Network Adapter

1. **Right-click** Kali Linux VM → **Settings**

2. Select **"Network Adapter"**

3. **Network connection:**
   - Select **"Custom: Specific virtual network"**
   - Choose **VMnet2** (or your host-only network)

4. Click **OK**

5. **Start Kali Linux VM**

6. **Verify network configuration** in terminal:
   ```bash
   ip addr show
   ```
   or
   ```bash
   ifconfig
   ```

7. **Optional: Set Static IP** (recommended for lab):
   ```bash
   sudo nano /etc/network/interfaces
   ```

   Add:
   ```
   auto eth0
   iface eth0 inet static
       address 192.168.100.10
       netmask 255.255.255.0
   ```

   Save and restart networking:
   ```bash
   sudo systemctl restart networking
   ```

**Screenshot Reference:** `screenshots/kali-network-config.png`

***

### Configure Metasploitable2 Network Adapter

1. **Right-click** Metasploitable2 VM → **Settings**

2. Select **"Network Adapter"**

3. **Network connection:**
   - Select **"Custom: Specific virtual network"**
   - Choose **VMnet2** (same as Kali Linux)[16]

4. Click **OK**

5. **Start Metasploitable2 VM** and login (`msfadmin`/`msfadmin`)

6. **Set Static IP Address:**
   ```bash
   sudo nano /etc/network/interfaces
   ```

   Modify to:
   ```
   auto eth0
   iface eth0 inet static
       address 192.168.100.100
       netmask 255.255.255.0
   ```

7. **Save and exit** (Ctrl+X, Y, Enter)

8. **Restart networking:**
   ```bash
   sudo /etc/init.d/networking restart
   ```

9. **Verify IP address:**
   ```bash
   ifconfig
   ```
   Should show: `192.168.100.100`

**Screenshot Reference:** `screenshots/metasploitable2-network-config.png`

***

### Test Network Connectivity

From **Kali Linux**, test connection to Metasploitable2:

```bash
ping 192.168.100.100
```

You should see successful ping responses

**Screenshot Reference:** `screenshots/ping-test-success.png`

***

### Network Topology Diagram

```
┌─────────────────────────────────────────┐
│         Host Computer (Windows)          │
│                                          │
│  VMware Virtual Network (VMnet2)         │
│  Network: 192.168.100.0/24               │
│  Type: Host-Only (Isolated)              │
└──────────────┬───────────────┬──────────┘
               │               │
       ┌───────▼──────┐  ┌────▼─────────┐
       │ Kali Linux   │  │Metasploitable│
       │              │  │      2       │
       │192.168.100.10│  │192.168.100   │
       │              │  │     .100     │
       │(Attacker VM) │  │ (Target VM)  │
       └──────────────┘  └──────────────┘
```

**Screenshot Reference:** Save this as `screenshots/network-topology-diagram.png`

***

# Troubleshooting

### Issue 1: "Virtualization is disabled in BIOS"

**Error Message:**
```
Intel VT-x is disabled
AMD-V is disabled
```

**Solution:**
1. Restart computer and enter BIOS
2. Enable Intel VT-x or AMD-V as described in Step 0
3. Save and restart

---

### Issue 2: VMware fails to start VM - "Cannot connect to virtual machine"

**Error Code:** `E_FAIL (0x80004005)`

**Solutions:**

**Option 1:** Restart VMware Services
```cmd
net stop VMwareHostd
net start VMwareHostd
```

**Option 2:** Run VMware as Administrator
- Right-click VMware → Run as Administrator

**Option 3:** Disable Hyper-V (conflicts with VMware)
```cmd
bcdedit /set hypervisorlaunchtype off
```
Then restart computer

---

### Issue 3: "No Internet in Kali Linux VM"

**Solution for NAT Network:**
1. VM Settings → Network Adapter
2. Select **"NAT"**
3. Click **OK**
4. In Kali, run:
   ```bash
   sudo dhclient eth0
   ```
5. Test: `ping 8.8.8.8`

***

### Issue 4: "Cannot ping between VMs"

**Solution:**

1. Verify both VMs are on the **same host-only network** (e.g., VMnet2)

2. Check firewall settings:
   
   **On Kali:**
   ```bash
   sudo ufw status
   sudo ufw allow from 192.168.100.0/24
   ```

   **On Metasploitable2:**
   ```bash
   sudo iptables -F
   ```

3. Verify IP addresses:
   ```bash
   ifconfig
   ```

4. Test connectivity:
   ```bash
   ping [target-ip]
   ```

***

### Issue 5: "Metasploitable2 won't boot"

**Solutions:**

1. **Check VM compatibility:**
   - Right-click VM → Settings → Options → General
   - Change Guest OS to **"Ubuntu"** if set incorrectly

2. **Increase memory allocation** (minimum 512 MB)

3. **Re-extract the ZIP file** - file may be corrupted

---

### Issue 6: "VMware kernel modules won't compile on Linux"

**Solution:**
```bash
sudo apt update
sudo apt install build-essential linux-headers-$(uname -r)
```
Then reinstall VMware

***

### Issue 7: "Slow VM performance"

**Solutions:**

1. **Increase RAM allocation:**
   - VM Settings → Memory → Increase to 4 GB+

2. **Allocate more CPU cores:**
   - VM Settings → Processors → Increase cores to 2-4

3. **Enable hardware virtualization:**
   - VM Settings → Processors → ✓ Virtualize Intel VT-x/EPT or AMD-V/RVI

4. **Disable unnecessary services in VM**

5. **Use SSD instead of HDD** for VM storage

***

### Issue 8: "Host-only adapter not working"

**Solution:**

1. **Recreate the host-only network:**
   - Edit → Virtual Network Editor
   - Delete existing host-only network
   - Click "Add Network"
   - Configure new host-only adapter

2. **Reset VMware networking:**
   ```cmd
   "C:\Program Files (x86)\VMware\VMware Workstation\vmnetcfg.exe"
   ```
   Click "Restore Defaults"

---

### Issue 9: "Shared folders not working"

**Solution:**

1. **Install VMware Tools:**
   - VM → Install VMware Tools
   - In VM, mount CD and run installer

2. **Enable shared folders:**
   - VM Settings → Options → Shared Folders
   - Select "Always enabled"
   - Add folder path

***

---

# 2. Linux Commands Cheat Sheet

# Linux Commands Cheat Sheet 

This cheat sheet covers the **foundational Linux commands** you learned during Task 1 (Days 1–12) of the ApexPlanet internship. Use it as a quick reference for file navigation, permissions, package management, networking basics, cryptography exercises, and tool usage.

---

## 1. File Navigation

| Command      | Description                          | Example               |
|--------------|--------------------------------------|-----------------------|
| `cd`         | Change directory                     | `cd /home/kali`       |
| `cd ..`      | Move up one directory level          | `cd ..`               |
| `ls -la`     | List files and directories           | `ls -la`              |
| `ls -lh`     | List with human-readable file sizes  | `ls -lh`              |
| `pwd`        | Print working directory              | `pwd`                 |
| `mkdir test` | Create directory                     | `mkdir test`          |
| `rm -r dir`  | Remove directory recursively         | `rm -r test/`         |

---

## 2. File Permissions & Ownership

| Command                 | Description                                | Example                        |
|-------------------------|--------------------------------------------|--------------------------------|
| `chmod 755 file`        | rwxr-xr-x (owner all, group/others rx)     | `chmod 755 script.sh`          |
| `chmod +x file`         | Add execute permission                     | `chmod +x script.sh`           |
| `chown user:group file`| Change owner and group                     | `chown kali:kali file.txt`     |
| `ls -l file`            | View detailed permissions                  | `ls -l file.txt`               |

**Permission digits:** 4 = r, 2 = w, 1 = x

---

## 3. Package Management (apt)

| Command                          | Description                      | Example                        |
|----------------------------------|----------------------------------|--------------------------------|
| `sudo apt update`                | Update package lists             | `sudo apt update`              |
| `sudo apt upgrade -y`            | Upgrade installed packages       | `sudo apt upgrade -y`          |
| `sudo apt install <pkg>`         | Install package                  | `sudo apt install nmap`        |
| `sudo apt remove <pkg>`          | Remove package                   | `sudo apt remove wireshark`    |
| `sudo apt autoremove -y`         | Remove unused dependencies       | `sudo apt autoremove -y`       |

---

## 4. Networking Basics

| Command                            | Description                          | Example                             |
|------------------------------------|--------------------------------------|-------------------------------------|
| `ifconfig`                         | Show network interfaces              | `ifconfig`                          |
| `ip addr show`                     | Display all network interfaces       | `ip addr show`                     |
| `ping -c 4 <host>`                 | Send 4 ICMP echo requests            | `ping -c 4 192.168.100.100`         |
| `traceroute <host>`                | Trace network path                   | `traceroute google.com`             |
| `netstat -tulnp`                   | List listening ports & services      | `netstat -tulnp`                    |
| `ss -tuln`                         | Socket statistics (modern netstat)   | `ss -tuln`                          |
| `arp-scan -l`                      | Discover hosts on local network      | `sudo arp-scan -l`                  |
| `nslookup <domain>`                | DNS query                            | `nslookup kali.org`                 |
| `sudo tcpdump -i eth0 -c 10`       | Capture 10 packets on eth0           | `sudo tcpdump -i eth0 -c 10`        |

---

## 5. Cryptography with OpenSSL

| Command                                                                                         | Description                    | Example                                                                                   |
|-------------------------------------------------------------------------------------------------|--------------------------------|-------------------------------------------------------------------------------------------|
| `openssl enc -aes-256-cbc -salt -in plain.txt -out enc.bin -pass pass:mypwd`                   | Symmetric encrypt file         | `openssl enc -aes-256-cbc -salt -in plain.txt -out enc.bin -pass pass:mypwd`              |
| `openssl enc -d -aes-256-cbc -in enc.bin -out dec.txt -pass pass:mypwd`                        | Symmetric decrypt file         | `openssl enc -d -aes-256-cbc -in enc.bin -out dec.txt -pass pass:mypwd`                  |
| `openssl genpkey -algorithm RSA -out private.pem -pkeyopt rsa_keygen_bits:2048`               | Generate RSA private key       | `openssl genpkey -algorithm RSA -out private.pem -pkeyopt rsa_keygen_bits:2048`          |
| `openssl rsa -in private.pem -pubout -out public.pem`                                          | Extract public key             | `openssl rsa -in private.pem -pubout -out public.pem`                                    |
| `openssl dgst -sha256 -sign private.pem -out sig.bin data.txt`                                 | Create SHA-256 signature       | `openssl dgst -sha256 -sign private.pem -out sig.bin data.txt`                           |
| `openssl dgst -verify public.pem -signature sig.bin data.txt`                                  | Verify signature               | `openssl dgst -verify public.pem -signature sig.bin data.txt`                            |

---

## 6. Tool Usage

| Tool / Command                   | Purpose                                     | Example                              |
|----------------------------------|---------------------------------------------|--------------------------------------|
| **Wireshark**                    | GUI packet capture and analysis             | Launch from Applications → Wireshark |
| **tshark**                       | CLI packet capture                          | `sudo tshark -i eth0 -w capture.pcap`|
| **nmap**                         | Network scanning and discovery              | `nmap -sV 192.168.100.100`           |
| **burp-suite**                   | Web app proxy & vulnerability testing       | Launch `burp-suite`                  |
| **netcat (nc)**                  | TCP/UDP connectivity and backdoors           | `nc -lvp 4444`                       |

---
---

# 3. OSI Model - Complete Notes

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
---

# 4. Symmetric Encryption Demo Script

## Symmetric Encryption Demo Script - OpenSSL Example
This Bash script demonstrates symmetric encryption and decryption using OpenSSL AES-256-CBC.
```
  bash
#!/bin/bash

# Symmetric Encryption Demo using OpenSSL

echo "=== Symmetric Encryption Demo ==="

# Create a test file
echo "This is a secret message" > plaintext.txt
echo "Original message:"
cat plaintext.txt

# Encrypt the file using AES-256-CBC
openssl enc -aes-256-cbc -salt -in plaintext.txt -out encrypted.bin -pass pass:mypassword
echo -e "\nFile encrypted successfully!"

# Decrypt the file
openssl enc -d -aes-256-cbc -in encrypted.bin -out decrypted.txt -pass pass:mypassword
echo -e "\nDecrypted message:"
cat decrypted.txt

# Cleanup
rm plaintext.txt encrypted.bin decrypted.txt
echo -e "\nDemo completed!"
```
`

---

# 5. Wireshark - Packet Analysis Guide

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
host 192.168.1.1                          # Capture traffic to/from specific host
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

# 6. Learning Outcomes

# Task 1 Learning Outcomes

This document summarizes the key skills, knowledge, and competencies acquired during **Task 1 (Days 1–12)** of the **ApexPlanet Cybersecurity & Ethical Hacking Internship**.

---

## 1. Cybersecurity Fundamentals

- **CIA Triad**: Mastered Confidentiality, Integrity, and Availability principles, forming the backbone of all security strategies.
- **Threat Landscape**: Identified and analyzed common threats—phishing, malware, DDoS, SQL injection, brute-force attacks, and ransomware.
- **Attack Vectors**: Understood social engineering, wireless attacks (Wi-Fi cracking, evil twins), and insider threat dynamics.

---

## 2. Lab Environment Setup

- **Virtualization**: Installed and configured VMware Workstation Pro, enabling isolated testbeds.
- **Kali Linux**: Deployed a Kali Linux VM, customized for penetration testing workflows.
- **Metasploitable2 & DVWA**: Set up vulnerable targets for hands-on exploitation practice.
- **Host-Only Networking**: Created an isolated virtual network to safely conduct attacks without impacting production environments.

---

## 3. Linux Command-Line Proficiency

- **File Navigation**: Efficient use of `cd`, `ls`, `pwd`, `mkdir`, and `rm` for directory and file operations.
- **Permissions & Ownership**: Applied `chmod`, `chown`, and `ls -l` to secure files and control access.
- **Package Management**: Managed software using `apt update`, `apt install`, and `apt upgrade` for tool installation and maintenance.

---

## 4. Networking Concepts

- **OSI Model**: In-depth understanding of all seven layers and their functions.
- **TCP/IP Suite**: Familiar with IP addressing, subnetting, NAT, and key protocols (TCP, UDP, ICMP).
- **Diagnostic Tools**: Utilized `ping`, `traceroute`, `netstat`, `ss`, `arp-scan`, `nslookup`, and `tcpdump` for network analysis.

---

## 5. Cryptography Basics

- **Symmetric Encryption**: Performed AES-256-CBC encryption/decryption using OpenSSL.
- **Asymmetric Encryption**: Generated RSA key pairs and managed public/private keys.
- **Hashing & Digital Signatures**: Created and verified SHA-256 signatures for data integrity.

---

## 6. Security Tool Familiarization

- **Wireshark**: Captured and analyzed network traffic with filters, coloring rules, and statistics.
- **Tshark**: Conducted command-line packet captures for automation.
- **Nmap**: Executed host discovery, port scanning, OS detection, and service enumeration.
- **Burp Suite**: Intercepted and tested web application traffic for OWASP Top 10 vulnerabilities.
- **Netcat**: Performed TCP/UDP connections, banner grabbing, and simple backdoor setups.

---


*End of Report*
