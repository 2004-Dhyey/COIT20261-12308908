# COIT20261 — DHCP Client & Server Lab  
**Name:** Dhyey Vyas  
**Student ID:** 12308908  
**Term:** 2026 Term 1  
**Week:** 07
---

# Task 1: DHCP Client

## Aim
Run a DHCP client to obtain an IP address.

---

## Topology Description
- 1 × OpenWRT Router (eth0 - LAN)
- 1 × Ethernet Switch
- 3 × Linux Hosts (Host1, Host2, Host3)

All devices are connected to the switch, which connects to the router via eth0.

---

## Procedure & Results

### 1. Project Creation
Project name: DHCP-Client-12308908

---

### 2. Router Configuration
OpenWRT router started successfully.  
Default DHCP server is active.

Command:
ip addr show eth0

Result:
192.168.1.1/24

---

### 3. Host 1 (Manual DHCP)

Check initial IP:
ip addr

Run DHCP:
udhcpc

Output:
udhcpc: lease of 192.168.1.x obtained

Verify:
ip addr

---

### 4. Host 2 (Auto DHCP Configuration)

File edited:
/etc/network/interfaces

Configuration:
auto eth0  
iface eth0 inet dhcp  
    hostname Host2  

Result: Host 2 automatically obtained IP on boot.

---

### 5. Host 3 (Packet Capture)

Steps:
- Started packet capture
- Ran DHCP client:
  udhcpc
- Stopped capture and analysed packets

---

## DHCP Packet Analysis

Observed DORA Process:

1. Discover — Host broadcasts request  
2. Offer — Router offers IP  
3. Request — Host requests offered IP  
4. Acknowledge — Router confirms lease  

---

## Task 1 Outputs

- DHCP-Client-12308908.gns3project  
- Network topology screenshot  
- Host1 DHCP screenshot  
- Host2 interfaces configuration  
- Packet capture (.pcap file)  

---

# Task 2: DHCP Server Basics

## Aim
View and modify DHCP server configuration and manage leases.

---

## Procedure & Results

### 1. Project Copy
DHCP-Server-Basics-12308908

---

### 2. View DHCP Configuration

Command:
cat /etc/config/dhcp

---

### 3. View via UCI

Command:
uci show dhcp.lan

Original configuration:
dhcp.lan=dhcp  
dhcp.lan.interface='lan'  
dhcp.lan.start='100'  
dhcp.lan.limit='150'  
dhcp.lan.leasetime='12h'  

---

### 4. Host 1 Lease

Command:
udhcpc

---

### 5. View Leases

Command:
cat /tmp/dhcp.leases

---

### 6. Change Lease Time

Commands:
uci set dhcp.lan.leasetime='2h'  
uci commit dhcp  
/etc/init.d/dnsmasq restart  

---

### 7. Host 2 Lease
Host 2 started and automatically received IP.

Check:
cat /tmp/dhcp.leases

---

### 8. Add Static Lease (Host 3)

Get MAC:
ip link

Configure:
uci add dhcp host  
uci set dhcp.@host[-1].name='Host3'  
uci set dhcp.@host[-1].mac='XX:XX:XX:XX:XX:XX'  
uci set dhcp.@host[-1].ip='192.168.1.200'  
uci commit dhcp  
/etc/init.d/dnsmasq restart  

---

### 9. Host 3 Lease

Run:
udhcpc

Result:
Assigned static IP: 192.168.1.200

---

### Final DHCP Configuration

dhcp.lan=dhcp  
dhcp.lan.interface='lan'  
dhcp.lan.start='100'  
dhcp.lan.limit='150'  
dhcp.lan.leasetime='2h'  

dhcp.@host[0]=host  
dhcp.@host[0].name='Host3'  
dhcp.@host[0].mac='XX:XX:XX:XX:XX:XX'  
dhcp.@host[0].ip='192.168.1.200'  

---

## Task 2 Outputs

- DHCP-Server-Basics-12308908.gns3project  
- Screenshot of original DHCP config  
- Screenshot of final DHCP config  
- Screenshot of DHCP leases (Host1, Host2, Host3)  

---

# Key Concepts

- DHCP automates IP allocation  
- udhcpc is a lightweight DHCP client  
- OpenWRT uses dnsmasq for DHCP  
- Static leases map MAC → IP  
- DHCP uses DORA (Discover, Offer, Request, Acknowledge)  

---

# Conclusion

This lab demonstrated:
- Manual and automatic DHCP configuration  
- DHCP packet flow analysis  
- DHCP server configuration using OpenWRT  
- Lease management and static IP assignment  

These are essential skills for real-world networking.

---
