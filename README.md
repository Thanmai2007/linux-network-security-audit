# linux-network-security-audit
A hands-on Linux network security audit using Linux networking commands, Nmap, and Wireshark to analyze network configuration, ports, and traffic.

# 🔐 Linux Network Security Audit

A hands-on Linux network security audit performed in a Kali Linux virtual machine using native Linux networking commands, Nmap, and Wireshark.

The project focuses on examining network configuration, routing, listening services, exposed TCP ports, and network traffic to document security-related observations.

---

## 🎯 Objective

The objective of this project was to perform a basic network security audit of a Kali Linux system by:

- Inspecting network interfaces and IP configuration
- Examining the routing table
- Identifying listening TCP/UDP services
- Scanning the local system with Nmap
- Capturing and analyzing network traffic with Wireshark
- Documenting the observations and findings

---

## 🛠️ Tools Used

- **Kali Linux**
- **Linux Networking Commands**
  - `ip addr`
  - `ip route`
  - `ss -tuln`
- **Nmap**
- **Wireshark**
- **VMware Workstation**

---

## 💻 Environment

| Component | Details |
|---|---|
| Operating System | Kali Linux |
| Virtualization | VMware Workstation |
| Network Interface | eth0 |
| IPv4 Address | 192.168.218.128/24 |
| Default Gateway | 192.168.218.2 |
| Nmap Version | 7.99 |
| Capture Interface | eth0 |

> The IP addresses shown in this project belong to the isolated/lab virtual network used during testing.

---

# 🔎 Methodology

## 1. Network Interface Analysis

The `ip addr` command was used to identify active network interfaces and their assigned addresses.

### Command

```bash
ip addr
