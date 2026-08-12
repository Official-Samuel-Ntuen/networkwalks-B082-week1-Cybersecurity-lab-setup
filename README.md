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
![Waqas](https://img.shields.io/badge/Instructor-Samuel_Ntuen-red)
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

Additional target machines can be added to the same virtual network in future projects.

