# Installation Guide

This document describes the installation process
for building the Active Directory lab environment
used in this project.

## Lab Requirements

### Hardware
- Minimum 8 GB RAM
- CPU virtualization enabled
- 40+ GB disk space

### Software
- VirtualBox
- Windows 10 ISO
- Windows Server ISO
- Ubuntu Server ISO
- Kali Linux ISO

## Virtual Machine Setup

| Machine | OS | Role |
|------|----|----|
| AD-DC | Windows Server | Domain Controller |
| Client | Windows 10 | Domain Client |
| Splunk | Ubuntu Server | Log Server |
| Attacker | Kali Linux | Attack Machine |

<br>

<p align="center">
<img width="940" height="509" alt="setup VMs" src="https://github.com/user-attachments/assets/b500a486-059f-435e-9b5f-f73adfed9717" />
  <br>
  <em align="center"> Virtual Machine Setup</em>
</p>
<br>

## Network Configuration
This section explains the network design
and configuration used in the lab environment.

All virtual machines in this lab are connected
to the same VirtualBox NAT Network.

This configuration allows:
- Internet access for updates and downloads
- Internal communication between virtual machines
- Isolation from the host local network

### NAT Network Setup

A NAT Network is created in VirtualBox to ensure
all machines reside in the same subnet.

Steps:
1. Open VirtualBox
2. Navigate to Tools → Network → NAT Networks
3. Create a new NAT Network
4. Enable DHCP (optional)

<p align="center">
<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/93e4268e-559b-400a-a31e-a6812415a14d" />
  <br>
  <em align="center"> Network Configuration </em>
</p>
<br>

### VM Adapter Configuration

Each virtual machine is configured
to use the same NAT Network.

Adapter settings:
- Adapter 1: NAT Network
- Network Name: ad-lab-network

### IP Addressing
The IP addressing strategy is designed
to ensure stability and reliable log forwarding.
- Ubuntu Splunk Server uses a static IP
  to ensure consistent log destination.
- Windows endpoints use DHCP.
- Kali Linux uses DHCP.

### Static IP Configuration (Splunk Server)
The following configuration assigns
a static IP address to the Splunk server network interface.
Edit netplan configuration:
```bash
sudo nano /etc/netplan/00-installer-config.yaml
```
<p align="center">
<img width="940" height="788" alt="image" src="https://github.com/user-attachments/assets/b22b522a-979f-4ce7-8674-f56890ecca8c" />
 <br>
  <em align="center"> Static IP Configuration UBUNTU SERVER </em>
</p>
<br>
### Connectivity Verification

Verify network connectivity by:
```bash
ip a
ping google.com
ping 192.168.14.10
```
<p align="center">
<img width="940" height="761" alt="image" src="https://github.com/user-attachments/assets/b4fdf0ca-1ef1-41f1-bd84-ac8df61335b7" />
 <br>
  <em align="center"> Connectivity Verification </em>
</p>
<br>

Successful responses confirm that:
- The network is properly configured
- Internet access is available
- Internal communication between VMs works correctly







