# Attack Simulation: Brute Force Attack on RDP Server

## ⚠️ Disclaimer
This project is created for educational purposes and ethical hacking practice only. Unauthorized access to computer systems is illegal. 
All activities in this lab were conducted in a controlled, private environment.

## Overview
This repository documents a simulated attack on a target server within a lab environment. The goal was to demonstrate how weak credentials can lead to unauthorized 
Remote Desktop Protocol (RDP) access.

1. Create Project Directory
First, open your terminal and create a dedicated directory named ad-project to keep all project files and logs organized.
```bash
mkdir ad-project
```
<p align="center">
<img width="940" height="80" alt="image" src="https://github.com/user-attachments/assets/86cfdaab-6581-4052-bca1-5adcd0c6a0d2" />
  <br>
  <em> Directory Attack </em>
</p>

To perform an effective brute-force attack, we need a comprehensive wordlist. In this lab, we will use the famous rockyou.txt wordlist which comes pre-installed in Kali Linux.

2. Copy the Wordlist to the Project Directory
Copy the wordlist from the default Kali directory to our ad-project folder:
```bash
cp /usr/share/wordlists/rockyou.txt.gz ~/ad-project/
```
<p align="center">
<img width="940" height="140" alt="image" src="https://github.com/user-attachments/assets/69bef5c8-79c0-41a2-8396-52874ad87a17" />
  <br>
  <em> Copy Password Attack </em>
</p>

3. Use the head command to take the top 20 passwords and save them into a new file named password.txt:
<p align="center">
<img width="777" height="198" alt="image" src="https://github.com/user-attachments/assets/a1bb0feb-3cb9-475f-afe7-28d011b12abe" />
  <br>
  <em> Copy Password Attack </em>
</p>

4. After successfully identifying the valid credentials,
the final step is to gain full remote access to the ADDC (Active Directory Domain Controller) server using the Remote Desktop Protocol (RDP).

- Install FreeRDP (If not already installed)
If you do not have xfreerdp installed on your Kali Linux system, you can install it using the following command:
```bash
sudo apt update
sudo apt install freerdp2-x11 -y
```
- Connect to the Server
Use the discovered username and password to initiate a remote session. Run the command below in your terminal
```bash
xfreerdp /v:192.168.14.101 /u:iganteng /p:P@ssword123 /cert:ignore /sec:rdp
```
- Execution Result
Once the command is executed, a new window will appear showing the Windows Server desktop environment.

<p align="center">
<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/d1fd82b8-3836-4977-9388-88ce5591007b" />
  <br>
  <em> Result Succes </em>
</p>
<br>

<p align="center">
<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/5e83eecf-74dd-48b6-8cd3-22c1ce3519cd" />

  <br>
  <em> Result view windows remote </em>
</p>
<br>

Success: The connection was established successfully, and we now have full remote control over the target ADDC server.









