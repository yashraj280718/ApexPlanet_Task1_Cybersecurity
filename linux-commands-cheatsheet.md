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
