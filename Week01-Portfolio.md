# COIT20261 – Portfolio
## Week 01 – GNS3 Introduction

**Name:** DHYEY VYAS  
**Student ID:** 12308908  
**Unit Code:** COIT20261  
**Term:** 2026 Term 1  
**Week:** 01  
**Date:** 13 March 2026  

---

## 1. Objective
The objective of this tutorial was to become familiar with the basic features of **GNS3**, including:

- Creating a new GNS3 project
- Adding a Linux host node
- Configuring a static IP address
- Adding annotations (text)
- Starting and stopping nodes
- Running Linux networking commands in the console

---

## 2. Software Setup
The following software was installed and used for this tutorial:

- **VirtualBox** – virtualization software
- **GNS3** – network simulation tool
- **GitHub** – for portfolio documentation and version control

---

## 3. GitHub Repository
A private GitHub repository was createD.


The repository stores weekly portfolio files and project outputs.

---

## 4. GNS3 Project Creation
A new GNS3 project was created with the name: 12308908-week-1


Steps performed:

1. Opened **GNS3**
2. Created a new project
3. Added a **Linux Host node**
4. Added **text annotations** with project details (student ID, name, date)
5. Configured the IP address before starting the node

---

## 5. Network Topology
The network topology consists of **one Linux host node** configured with a static IP address.

### Topology Screenshot

![Network Topology](GNS3-Intro-12308908-network.png)

---

## 6. IP Address Configuration
The IP address was configured in the Linux host by editing:


### Explanation
- **auto eth0** – automatically activates the interface  
- **iface eth0 inet static** – sets a static IP configuration  
- **address** – assigned IP address  
- **netmask** – network mask  
- **ip_forward=0** – disables IP forwarding so the node behaves like a normal host  

---

## 7. Starting the Node
After configuration:

1. Started the Linux host node
2. Opened the **Web Console**
3. Accessed the Linux terminal

---

## 8. Verifying the IP Address
Command used to verify the IP address:


### Console Screenshot

![IP Address Console](GNS3-Intro-12308908-ipaddress.png)

Output confirmed that **eth0** is assigned the IP address **10.10.1.1**.

---

## 9. Files Uploaded to GitHub
The following files were uploaded to the repository:

- `Week01-Portfolio.md`
- `GNS3-Intro-12308908.gns3project`
- `GNS3-Intro-12308908-network.png`
- `GNS3-Intro-12308908-ipaddress.png`

---

## 10. What I Learned
- How to create a **GNS3 project**
- How to add and configure a **Linux host node**
- How to configure a **static IP address in Linux**
- How to run basic Linux networking commands
- How to document work using **Markdown in GitHub**

---

## 11. Conclusion
This tutorial introduced the basic setup and configuration of a simple network using GNS3.  
It also demonstrated how GitHub and Markdown can be used to document networking and cybersecurity practical work professionally.
