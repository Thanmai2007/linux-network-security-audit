# linux-network-security-audit
A hands-on Linux network security audit using Linux networking commands, Nmap, and Wireshark to analyze network configuration, ports, and traffic.

# Linux Network Security Audit

A hands-on Linux network security audit performed in a Kali Linux virtual machine using Linux networking commands, Nmap, and Wireshark.

The project focuses on examining network configuration, routing, listening services, exposed TCP ports, and network traffic to document security-related observations.

---

## Objective

The objective of this project was to perform a basic network security audit of a Kali Linux system by:

- Inspecting network interfaces and IP configuration
- Examining the routing table
- Identifying listening TCP/UDP services
- Scanning the local system with Nmap
- Capturing and analyzing network traffic with Wireshark
- Documenting the observations and findings

---

## Tools Used

- Kali Linux
- Linux Networking Commands
  - `ip addr`
  - `ip route`
  - `ss -tuln`
- Nmap
- Wireshark
- VMware Workstation

---

## Environment

| Component | Details |
|---|---|
| Operating System | Kali Linux |
| Virtualization | VMware Workstation |
| Network Interface | eth0 |
| IPv4 Address | 192.168.218.128/24 |
| Default Gateway | 192.168.218.2 |
| Nmap Version | 7.99 |
| Capture Interface | eth0 |

The IP addresses shown in this project belong to the virtual network used during testing.

---

## Methodology

## 1. Network Interface Analysis

The ip addr command was used to identify active network interfaces and their assigned addresses.

#### Command

bash
ip addr

Observations

Active interface: eth0

IPv4 address: 192.168.218.128/24

Broadcast address: 192.168.218.255

Loopback address: 127.0.0.1

Interface state: UP


Screenshot

#### Screenshot

![IP Address Configuration](screenshots/01-ip-addr.jpeg)


---

2. Routing Table Analysis

The ip route command was used to examine the system's routing configuration.

Command

ip route

Observations

Local network: 192.168.218.0/24

Default gateway: 192.168.218.2

Network interface: eth0


The default route indicates that traffic destined outside the local network is forwarded through the configured gateway.

Screenshot

#### Screenshot

![routing table ](screenshots/02-ip-route.jpeg)




---

3. Listening Port Analysis

The ss command was used to check for currently listening TCP and UDP sockets.

Command

ss -tuln

Observations

No listening TCP or UDP sockets were displayed during the audit.

This indicates that no network services were listening on TCP/UDP sockets at the time of this check.

Screenshot

#### Screenshot

![Listening port analysis](screenshots/03-ss-tuln.jpeg)



---

4. Nmap Localhost Scan

Nmap was used to scan the local Kali system and identify accessible TCP services.

Command

nmap -sV 127.0.0.1

Scan Results

Target: 127.0.0.1

Host status: Up

Ports scanned: 1,000

Open TCP ports: 0

Closed TCP ports: 1,000

Services detected: None


The Nmap results were consistent with the ss -tuln observation that no TCP services were listening during the audit.

Screenshot

#### Screenshot

![NMNAP localist scan ](screenshots/04-nmap-scan.jpeg)



---

5.Wireshark Traffic Analysis

Wireshark was used to capture and inspect network traffic on the eth0 interface.

A .pcapng capture file was saved for further examination.

Capture Overview

The initial capture showed multiple types of network traffic, including ARP and NTP packets.

Screenshot

#### Screenshot

![While shark traffic analysis](screenshots/05-wireshark-overview.jpeg)



---

6.ICMP Analysis

ICMP traffic was generated using the ping command and analyzed in Wireshark.

Command

ping -c 4 192.168.218.2

Wireshark Filter

icmp

Observations

ICMP Echo Requests were observed

ICMP Echo Replies were observed

Source: 192.168.218.128

Destination: 192.168.218.2


The request and reply exchange demonstrated successful ICMP communication between the Kali VM and its default gateway.

Screenshot

#### Screenshot

![ICMP analysis](screenshots/06-icmp.jpeg)



---

7.ARP Analysis

ARP traffic was filtered in Wireshark to observe address resolution on the local network.

Wireshark Filter

arp

Observations

ARP request and reply packets were observed.

The capture included ARP traffic used to resolve the gateway's IPv4 address to its corresponding MAC address.

Screenshot

#### Screenshot

![ARP analysis](screenshots/07-wireshark-overview.jpeg)



---

8.DNS Analysis

DNS traffic was generated using nslookup and analyzed in Wireshark.

Command

nslookup example.com

Wireshark Filter

dns

Observations

DNS queries and responses were observed

Source: 192.168.218.128

DNS resolver/gateway: 192.168.218.2

A and AAAA DNS queries were observed

DNS traffic was transported using UDP


Screenshot

#### Screenshot

![DNS analysis](screenshots/08-wireshark-dns.jpeg)


---

Audit Findings

Area	Tool / Command	Finding

Network Interface	ip addr	eth0 active with 192.168.218.128/24
Routing	ip route	Default gateway 192.168.218.2
Listening Services	ss -tuln	No listening TCP/UDP sockets displayed
Port Scan	Nmap	0 open TCP ports among 1,000 scanned
ICMP	Wireshark	Echo request/reply traffic observed
ARP	Wireshark	ARP request/reply traffic observed
DNS	Wireshark	DNS queries and responses observed



---

Security Observations

Based on the scope and tools used during this audit:

1. No listening TCP/UDP sockets were displayed by ss -tuln.


2. Nmap identified no open TCP ports among its default 1,000-port scan of 127.0.0.1.


3. ICMP communication with the default gateway was successfully observed.


4. ARP address-resolution traffic was observed on the local network.


5. DNS queries and responses were successfully captured and analyzed.


6. Network traffic could be inspected at the packet level using Wireshark.



 Audit Findings
Area
Tool / Command
Finding
Network Interface
ip addr
eth0 active with 192.168.218.128/24
Routing
ip route
Default gateway 192.168.218.2
Listening Services
ss -tuln
No listening TCP/UDP sockets displayed
Port Scan
Nmap
0 open TCP ports among 1,000 scanned
ICMP
Wireshark
Echo request/reply traffic observed
ARP
Wireshark
ARP request/reply traffic observed
DNS
Wireshark
DNS queries and responses observed
 
 Security Observations
Based on the scope and tools used during this audit:
No listening TCP/UDP sockets were displayed by ss -tuln.
Nmap identified no open TCP ports among its default 1,000-port scan of 127.0.0.1.
ICMP communication with the default gateway was successfully observed.
ARP address-resolution traffic was observed on the local network.
DNS queries and responses were successfully captured and analyzed.
Network traffic could be inspected at the packet level using Wireshark.
