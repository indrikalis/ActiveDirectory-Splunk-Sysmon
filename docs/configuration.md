# Configuration Guide

This document describes the configuration steps
required to prepare the Active Directory lab
for centralized logging, monitoring,
and security analysis using Sysmon and Splunk.

---

## 1. Active Directory Domain Controller Configuration

The Windows Server machine is configured
as an Active Directory Domain Controller (AD DC).

###  Install Active Directory Domain Services (AD DS)

- Open **Server Manager**
- Add Roles and Features
- Select **Active Directory Domain Services**
- Complete the installation


<p align="center">
<img width="940" height="201" alt="image" src="https://github.com/user-attachments/assets/542926e8-7847-4e40-962c-d2889a3cf36d" />
  <br>
  <em>AD DS Role Installation</em>
</p>

---
## 2. User and Group Configuration

Domain users and groups are created
to simulate a basic enterprise environment.

### Create Domain Users

- Create one or more domain users
- Assign secure passwords
- Enable user accounts

<p align="center">
  <img width="940" height="656" alt="image" src="https://github.com/user-attachments/assets/e7bb3493-d777-49d6-8705-175e9944332e" />

  <br>
  <em>Domain User Creation</em>
</p>

## 3. Windows 10 Domain Join Configuration

The Windows 10 client machine is joined
to the Active Directory domain.

###  DNS Configuration

- Set DNS server to the Domain Controller IP
- Verify DNS resolution

<p align="center">
  <img width="700" height="864" alt="image" src="https://github.com/user-attachments/assets/4ba1db3b-1ba3-44b7-aa9b-6f9a5250cef3" />

  <br>
  <em>DNS Configuration on Windows 10</em>
</p>

### Join Windows 10 to Domain

- Join the client machine to the domain
- Reboot the system
- Login using domain credentials


<p align="center">
  <img width="644" height="755" alt="image" src="https://github.com/user-attachments/assets/3e506056-803e-4106-bb3c-aef668ee8a1b" />

  <br>
  <em>Windows 10 Joined to Domain</em>
</p>

---


## 4. Sysmon Configuration

Sysmon is installed and configured
on all Windows endpoints
to enhance event visibility.

### Sysmon Installation

- Download Sysmon from Microsoft Sysinternals
- Install Sysmon with configuration file
- Verify Sysmon service is running


<p align="center">
  <img width="940" height="772" alt="image" src="https://github.com/user-attachments/assets/a1754930-57e3-4658-9294-fa6ea18fc5f5" />
  <br>
  <em>Sysmon Splunk </em>
</p>


### Sysmon Service Verification

- Verify Sysmon service status
- Confirm logs are being generated

<p align="center">
  <img width="940" height="799" alt="image" src="https://github.com/user-attachments/assets/8cd4a7a7-fd6d-40ce-bd20-8ea402da521a" />

  <br>
  <em>Sysmon Service Status</em>
</p>

## 5. Splunk Universal Forwarder Configuration

Splunk Universal Forwarder is configured
to forward logs from Windows endpoints
to the Splunk server.

###  Forwarder Installation

- Install Splunk Universal Forwarder
- Configure Splunk server IP and port
- Start the forwarder service


<p align="center">
  <img width="940" height="455" alt="image" src="https://github.com/user-attachments/assets/879bbcb6-c91b-4122-98c5-b6eb642bd2b2" />

  <br>
  <em>Splunk Forwarder Installation</em>
</p>

---

## 6. Log Verification in Splunk

Log forwarding is verified
by confirming the presence
of Windows and Sysmon logs
in the Splunk dashboard.


<p align="center">
  <img width="919" height="434" alt="image" src="https://github.com/user-attachments/assets/3ae47474-6d34-43c4-8df7-5b91092c989a" />

  <br>
  <em>Log Verification in Splunk</em>
</p>

---

## 7. Configuration Completion Criteria

The configuration is considered successful if:
- Domain Controller is operational
- Clients can authenticate to the domain
- Sysmon is generating logs
- Splunk receives logs from all endpoints


