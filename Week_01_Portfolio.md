# GNS3 Introduction Lab Portfolio

> **Project:** GNS3-Intro-12220267\
> **Student Name:** Patrick Lorian\
> **Student ID** 12220267\
> **Campus:** Rockhampton\
> **Date:** 11/03/2026

## Lab Overview
This lab introduces the GNS3 network simulator. The objective was to create a simple network project with a single Linux host, this..

## Host Configuration
| **Step** | **Task** | **Description** | **Status** |
|---|---|---|---|
| 1 | Create New Project | Created project named `GNS3-Intro-<12220267>` in GNS3 |  Done |
| 2 | Add Linux Host | Dragged a single Linux Host node onto the workspace |  Done |
| 3 | Add Project Info Text | Added text showing project title, name, student ID, date, unit code, campus, and teacher |  Done |
| 4 | Select IP Address | Selected static IP address `10.10.1.1` for the host |  Done |
| 5 | Add IP Label | Added text near the node displaying the IP address `10.10.1.1` |  Done |
| 6 | Configure Static IP | Edited `/etc/network/interfaces` to set static IP before starting the node |  Done |
| 7 | Start the Node | Started the Linux host node in GNS3 |  Done |
| 8 | Open Web Console | Opened a web console in a new browser tab |  Done |
| 9 | Verify IP Address | Ran `ip address show` to confirm the IP address configuration | Done |
| 10 | Close Project | Verified all outputs, documented commands and learnings, then closed the project | Done |

## Network Interface Configuration
### File: '/etc/network/interfaces'
The following configuration was applied to the 'etc/network/interfaces' file **before** starting the node:

'''
bash
# Static config for eth0
auto eth0
iface eth0 inet static
    address 10.10.1.1
    netmask 255.255.255.0
    up sysctl net.ipv4.ip_forward=0
'''
### Configuration Explained

| **Line** | **Command** | **Purpose** |
|---|---|---|
| 1 | `auto eth0` | Automatically brings up the eth0 interface at boot |
| 2 | `iface eth0 inet static` |  |
| 3 | `address 10.10.1.1` |  |
| 4 | `netmask 255.255.255.0` |  |
| 5 | `up sysctl net.ipv4.ip_forward=0` |  |

### Purpose of disabling IP Forwarding?
The main purpose of disabling IP forwarding is to enhance network security by preventing a device from acting as a router and passing traffic between different networks.

---

## Commands Used
| S.N. | Command | **Purpose** |
|---|---|---|
| 1 | `ip address show` |  |
| 2 | `cat /etc/network/interfaces` |  |
| 3 | `sysctl net.ipv4.ip_forward` |  |

### Example Output: `ip address show`

```
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever

3: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UNKNOWN qlen 1000
    link/ether 02:42:b9:24:73:00 brd ff:ff:ff:ff:ff:ff
    inet 10.10.1.1/24 scope global eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::42:b9ff:fe24:7300/64 scope link
       valid_lft forever preferred_lft forever
```

### Output Explained

| **Field** | **Value** | **Meaning** |
|---|---|---|
| Interface | eth0 | Ethernet interface |
| State | UP, LOWER_UP | |
| MTU | 1500 | Maximum Transmission Unit (standard Ethernet) |
| MAC Address | 02:42:b9:24:73:00 |  |
| IPv4 Address | 10.10.1.1/24 | Static IP address with /24 subnet |
| IPv6 Address | fe80::42:b9ff:fe24:7300/64 |  |

---

## Screenshots 

### Screenshot 1: GNS3 Network Topology

> This screenshot shows the GNS3 workspace with the Linux host node, project title, student details, and IP address label.

![Network Topology](screenshots/GNS3-Intro-studentid-network.png)

**File:** `GNS3-Intro-<studentid>-network.png`

>  *Replace the image path above with your actual screenshot file path after uploading.*

---

### Screenshot 2: Console Output — IP Address Verification

> This screenshot shows the web console output of the `ip address show` command, confirming the static IP address `10.10.1.1` is correctly assigned to eth0.

![IP Address Console](screenshots/GNS3-Intro-studentid-ipaddress.png)

**File:** `GNS3-Intro-<studentid>-ipaddress.png`

>  *Replace the image path above with your actual screenshot file path after uploading.*

---



##  Key Knowledge & Skills Developed

### Networking Concepts

| **S.N.** | **Concept** | **Learning Outcomes** |
|---|---|---|
| 1 | Static IP Configuration | How to manually assign an IP address to a Linux network interface using `/etc/network/interfaces` |
| 2 | Subnet Mask |  |
| 3 | IP Forwarding |  |
| 4 | Network Interfaces |  |


### Technical Skills

| **S.N.** | **Skill** | **Description** |
|---|---|---|
| 1 | GNS3 Project Setup | Creating new projects, ... |
| 2 | Linux CLI | Using commands like `ip address show`,.. |
| 3 | File Editing | Editing the `/etc/network/interfaces` configuration file to ... |
| 4 | Network Verification | Confirming IP settings by reading and interpreting `ip address show` output |
| 5 | Documentation |  | Documented the full lab process, including commands, configurations, and screenshots, in a clear and structured format to ensure the work can be easily understood and replicated._



---

##  Reflection

### Key Success or Positive Outcomes?

- Successfully configured a static IP address (***10.10.1.1***) on a Linux host within GNS3 using the ***/etc/network/interfaces*** file
- Verified network configuration using the ***ip address show*** command and correctly interpreted the output
- Gained hands-on experience using GNS3 to create and manage a bsaic network topology
- Improved understanding of how network interfaces (like eth0) operate in a Linux environment
- Learned the importance of planning and coumenting each configuration step for troubleshooting and reproducability
### Challenges faced and how you solved it?

- Initially unsure about the correct syntax for editing the ***/etc/network/interfaces*** file
> Solved by reviewing the examples and carefully following the correct indentation and structure.
- Understanding the meaning of the ip address show output (e.g., flags like UP, LOWER_UP, and IPv6 entries).
> Resolved by breaking down each line and researching what each field represents.
- Forgetting to configure the IP address before starting the node, which caused incorrect results.
> Fixed by restarting the node after applying the correct configuration.

---

##  Reference

- GNS3 Documentation: [https://docs.gns3.com](https://docs.gns3.com)

---

##  Repository Structure (You can follow these structure by creating or uploading new files )

```
GNS3-Intro-<studentid>/week1
├── Week1-README.md                          ← This portfolio file
├── GNS3-Intro-<studentid>-network.png       ← Network topology screenshot
└── GNS3-Intro-<studentid>-ipaddress.png     ← Console IP address screenshot
└── GNS3-Intro-<studentid>.gns3project       ← Exported GNS3 project file
```

---
