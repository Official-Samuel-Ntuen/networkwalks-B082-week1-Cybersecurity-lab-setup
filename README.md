# 🖥️ Cybersecurity & Pentesting Lab Setup
**Building an isolated virtual lab for penetration testing and ethical hacking practice**
---
![Skill](https://img.shields.io/badge/Skill-Cybersecurity-red)
![Ver](https://img.shields.io/badge/VirtualBox-v7.2.8-blue)
![Kali](https://img.shields.io/badge/Kali_Linux-v2026.1-purple)
![Skill](https://img.shields.io/badge/Skill-Linux-red)
![Network](https://img.shields.io/badge/Network-192.168.0.0/24-black)
![Skill](https://img.shields.io/badge/Penetration_Testing-Skill-red)
![Skill](https://img.shields.io/badge/Skill-Virtualization-red)
![GitHub](https://img.shields.io/badge/GitHub-Official--Samuel--Ntuen-black?logo=github)
![Kali](https://img.shields.io/badge/Kali_Linux-v2026.1-purple)
![NetworkWalks](https://img.shields.io/badge/NetworkWalks-orange)
![Ethical](https://img.shields.io/badge/Ethical_Hacking-darkgreen)
![Waqas](https://img.shields.io/badge/-Samuel_Ntuen-red)
---

## 📌 Project Overview

This project focuses on setting up a virtual cybersecurity and penetration-testing laboratory using VirtualBox and Kali Linux.

The purpose of the lab is to create a controlled and isolated environment where I can safely practice cybersecurity tools, network scanning, reconnaissance, vulnerability assessment, and other security testing activities without putting my real machine or home network at risk.

The lab is configured on a private virtual network so that additional machines can be added later and used as targets for authorized security testing.

---

## 🎯 Objectives

- Install and configure VirtualBox 7.2.8 on Kali Linux
- Install Kali Linux 2026.1 as a virtual machine
- Create a private NAT Network for the cybersecurity lab
- Configure network connectivity for the VMs
- Assign a consistent IP address to the Kali VM
- Enable Intel VT-x hardware virtualization in BIOS
- Verify network connectivity and DNS resolution
- Take a clean VM snapshot for recovery
- Document the complete setup process including real problems faced
- Prepare the environment for future cybersecurity projects

---

## 🛡️ Purpose of the Lab

The lab provides an isolated and controlled environment for cybersecurity learning and authorized security testing.

It can be used for activities such as:

- Network reconnaissance
- Port scanning
- Vulnerability assessment
- Packet analysis
- Web security testing
- Exploitation practice
- Security tool experimentation

⚠️ **Important:** This laboratory must only be used for systems that you own or have explicit permission to test. Do not use the lab or its tools to attack unauthorized systems.

---

## 🏗️ Lab Architecture
The setup consists of my Laptop running a dual boot of Windows 11 and Kali Linux. Inside Kali Linux, VirtualBox hosts two virtual machines — Windows 11 and Kali Linux — connected through a NAT Network for isolated cybersecurity practice.

<img width="1358" height="723" alt="Screenshot_2026-08-12_01-58-52" src="https://github.com/user-attachments/assets/f7b46563-100a-4eb9-842d-71424d1b6566" /> 

Additional target machines can be added to the same virtual network in future projects.

---

## ⚙️ Lab Configuration

| 🧩 Component | ⚙️ Configuration |
|---|---|
| 🖥️ Host Machine | HP EliteBook 840 G3 |
| ⚡ Processor | Intel Core i5 |
| 🧠 Host RAM | 8GB |
| 💾 SSD Size | 256 GB |
| 💻 Host OS | Kali Linux 2026.1 (Dual Boot with Windows 11) |
| 🧰 Hypervisor | Oracle VirtualBox 7.2.8 |
| 🖥️ VM 1 | Windows 11 Enterprise Evaluation |
| 🐉 VM 2 | Kali Linux 2026.1 |
| 🧠 VM RAM | 4096 MB each |
| ⚡ VM CPUs | 2 per VM |
| 🌐 Kali IP Address | 192.168.0.102 |
| 🌐 Virtual Network | NAT Network |
| 📡 Network Address | 10.0.0.0/24 |
| 🌍 DNS Server | 8.8.8.8 |
| 🚪 Default Gateway |	10.0.0.1
| 🔮 Future VM Range |	10.0.0.3–10.0.0.99
---

# 🪜 Lab Setup Procedure

## Step 1. Install VirtualBox on Kali Linux

VirtualBox was installed on Kali Linux as the hypervisor to host the virtual machines.

```bash
sudo apt update
sudo apt install virtualbox -y
```
---

## Step 2. Create NAT Network in VirtualBox

A dedicated NAT Network was created in VirtualBox so that virtual machines can communicate with each other while also having outbound internet connectivity.
Configuration:

Network Name: NatNetwork
IPv4 Prefix: 10.0.0.0/24
DHCP: Enabled
IPv6: Disabled

<img width="1351" height="734" alt="Screenshot_2026-08-11_20-33-55" src="https://github.com/user-attachments/assets/c150a263-c1a1-4574-9cd2-ac182273d26f" />


A NAT Network was selected because multiple virtual machines connected to the same NAT Network can communicate with one another while also having outbound network connectivity.
This will allow future attacker and target VMs to communicate within the lab.

---

## Step 3. Enable Intel VT-x in BIOS

Before starting any VM, I needed to enable hardware virtualization in the BIOS.

1. Restarted the laptop
2. Pressed **F10** to enter BIOS
3. Navigated to **Advanced → System Options**
4. Enabled **Virtualization Technology (VTx)**
5. Enabled **Virtualization Technology for Directed I/O (VTd)**
6. Saved and exited BIOS

---

## Step 4. Fix VirtualBox Kernel Driver

After installing VirtualBox, the kernel driver was not loaded. I fixed it by running:

```bash
sudo apt install virtualbox-dkms -y
sudo apt install linux-headers-amd64 -y
sudo dpkg-reconfigure virtualbox-dkms
sudo modprobe vboxdrv
```
---

## Step 5. Create Windows 11 Virtual Machine

I created a new virtual machine in VirtualBox for Windows 11.

**Configuration:**
- VM Name: Windows 11
- ISO: Windows 11 Enterprise Evaluation
- RAM: 4096 MB
- CPUs: 2
- Disk: 80 GB
- Network: NAT Network

---

## Step 6. Create Kali Linux Virtual Machine

After Windows 11 was set up, I created a second virtual machine for Kali Linux.

**Configuration:**
- VM Name: Kali Linux
- ISO: kali-linux-2026.1-installer-amd64.iso
- RAM: 4096 MB
- CPUs: 2
- Disk: 21.5 GB
- Desktop Environment: Xfce with default tools
- Network: NAT Network

<img width="1351" height="650" alt="Screenshot_2026-08-11_20-42-28" src="https://github.com/user-attachments/assets/ceb39a96-e9b0-4b79-b2ef-76a07e92a9c8" />
A shared folder was also configured for transferring required files between the host operating system and the Kali VM.

---

## Step 7. Configure Kali Linux Network
The Kali Linux network configuration was checked and configured with a consistent IPv4 address.

Example configuration:
```bash
IP Address: 10.0.0.2
Subnet Mask: 255.255.255.0
Gateway: 10.0.0.1
DNS: 8.8.8.8
```
<img width="1357" height="704" alt="Screenshot_2026-08-11_22-09-57" src="https://github.com/user-attachments/assets/37af24f8-7bc5-4672-90c0-10956aa9ba43" />

A consistent IP address makes it easier to document the lab and reference the Kali machine in future exercises.

---

## Step 8. Take a Clean VM Snapshot

After completing the initial configuration, a VirtualBox snapshot was taken for both VMs.
```bash
Snapshot Name: Clean Lab - Initial Setup
```
This snapshot represents the clean baseline of the laboratory. If a future exercise changes or damages the VM configuration, the machine can be restored to this baseline.

---
# 🔎 Lab Verification

| ✅ Test | 🧾 Command | 🎯 Result |
|---|---|---|
| 🌐 Check IP address | `ip a` | 192.168.0.102 displayed |
| 🌍 Test internet | `ping 8.8.8.8` | Successful replies |
| 🔎 Test DNS | `nslookup google.com` | Domain resolved |
| 🧰 Verify Nmap | `nmap --version` | Nmap version displayed |
| 🖥️ Windows 11 VM | Start VM | Desktop loaded successfully |
| 🐧 Kali Linux VM | Start VM | Kali installed successfully |
🔄 Verify snapshot | Restore snapshot and run ip a | Baseline configuration restored
```
Example Results
IP Address:
10.0.0.2/24

Gateway:
10.0.0.1

DNS:
8.8.8.8
```
---

# 🐞 Problems Faced & Solutions

## Problem 1 — VirtualBox Kernel Driver Not Installed

**Error:**

Kernel driver not installed (rc=-1908)


**Solution:** Installed the correct kernel headers and rebuilt the VirtualBox DKMS module:
```bash
sudo apt install linux-headers-amd64 -y
sudo dpkg-reconfigure virtualbox-dkms
sudo modprobe vboxdrv
```

## Problem 2 — VT-x Disabled in BIOS

**Error:**

VT-x is disabled in the BIOS for all CPU modes


**Solution:** 
The issue was resolved by:

Restarting the computer.
1. Entering BIOS/UEFI settings.
2. Enabling Intel VT-x / hardware virtualization.
3. Saving the configuration.
4. Restarting the computer.
5. Starting the Kali VM again.
After enabling virtualization, the VM started successfully.

## Problem 3 — DNS Not Working in Kali Linux VM

**Problem:** After configuring the network, my Kali VM had no working internet access through domain names. The IP address was working but DNS resolution was failing.

**Error:**

ping: google.com: Temporary failure in name resolution


**What I noticed:** Pinging 8.8.8.8 directly worked fine, which meant my internet connection was active. However, pinging google.com failed because DNS was not resolving domain names to IP addresses.

**Solution:** I manually configured the DNS servers using nmcli:

```bash
sudo nmcli connection modify "Wired connection 1" ipv4.dns "1.1.1.1 8.8.8.8" ipv4.ignore-auto-dns yes
sudo nmcli connection down "Wired connection 1"
sudo nmcli connection up "Wired connection 1"
```

**Verification:**
```bash
ping -c 4 google.com
```

**Result:**

64 bytes from google.com: icmp_seq=1 ttl=118
4 packets transmitted, 4 received, 0% packet loss


After setting the DNS servers manually to 1.1.1.1 and 8.8.8.8, domain name resolution started working correctly.

---

# 💡 What I Learned

### 1. Hardware Virtualization
I learned that Intel VT-x must be enabled in BIOS before VirtualBox can run 64-bit virtual machines. Without this, all VMs fail to start regardless of how VirtualBox is configured.

### 2. VirtualBox Kernel Modules
I learned that VirtualBox on Linux requires kernel modules to be compiled and loaded. If the kernel headers are missing, the modules fail to build and VMs cannot start.

### 3. NAT vs NAT Network
I learned the difference between NAT and NAT Network in VirtualBox. A NAT Network allows multiple VMs to communicate with each other while still having internet access, making it perfect for a cybersecurity lab with attacker and target machines.

### 4. DNS Configuration
I learned the difference between internet connectivity and DNS resolution. A machine can have a working IP connection (ping 8.8.8.8 succeeds) but still fail to resolve domain names if DNS is not configured correctly. I fixed this by manually setting DNS servers 1.1.1.1 and 8.8.8.8 using nmcli in Kali Linux.

### 5. VM Snapshots
I learned that a clean snapshot should be created before performing risky or experimental activities. This provides a known-good recovery point for future cybersecurity exercises.

### 6. Documentation
I learned that documenting every step including problems and solutions is just as important as the technical work itself. Real problems and real solutions make a project authentic and valuable.

---

# 🔐 Security & Ethical Use

This laboratory is intended strictly for educational purposes only. 

---

# 🔗 Tools & Resources

- **VirtualBox:** https://virtualbox.org
- **Kali Linux:** https://kali.org/get-kali
- **Windows 11 ISO:** https://microsoft.com

---

# 👤 Author

**Samuel Ntuen**

Cybersecurity Intern — Batch B082

LinkedIn: *(add your LinkedIn link here)*

---

# 📌 Project Information
Program Name: Cybersecurity at Networkwalks | Week: 01 | Project: Cybersecurity & Pentesting Lab Setup | Repository: GitHub
