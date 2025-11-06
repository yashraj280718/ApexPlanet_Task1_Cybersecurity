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
   - **Windows**: `VMware-workstation-full-xx.x.x-xxxxxxx.exe`
   - **Linux**: `VMware-Workstation-Full-xx.x.x-xxxxxxx.bundle`

**Screenshot Reference:** `screenshots/vmware-download-page.png`

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

**Screenshot Reference:** `screenshots/kali-vm-iso-selection.png`

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

## Step 4: Network Configuration (Host-Only Adapter)

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

### Screenshot Checklist

Ensure you have captured and saved these screenshots in the `screenshots/` folder:

- [ ] `bios-virtualization-enabled.png`
- [ ] `vmware-download-page.png`
- [ ] `vmware-installation-complete.png`
- [ ] `vmware-first-launch.png`
- [ ] `kali-iso-download.png`
- [ ] `kali-vm-iso-selection.png`
- [ ] `kali-vm-created.png`
- [ ] `kali-boot-menu.png`
- [ ] `kali-desktop.png`
- [ ] `kali-system-update.png`
- [ ] `metasploitable2-extracted-files.png`
- [ ] `metasploitable2-imported.png`
- [ ] `metasploitable2-settings.png`
- [ ] `metasploitable2-login.png`
- [ ] `vmware-hostonly-network.png`
- [ ] `kali-network-config.png`
- [ ] `metasploitable2-network-config.png`
- [ ] `ping-test-success.png`
- [ ] `network-topology-diagram.png`

***
