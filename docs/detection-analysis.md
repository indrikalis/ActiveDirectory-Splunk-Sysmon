# Detection & Analysis using  
  
In this phase, we act as a Security Analyst to detect and analyze the previous brute-force attack. By monitoring Windows Event Logs ingested into Splunk,
we can identify the attack patterns, the source IP, and the compromised account.

## 1. Log Analysis and Event Correlation
After the attack simulation, we analyzed the logs ingested into Splunk from the target endpoint. 
By examining the EventCode distribution, we can correlate the activities that occurred during the breach.

<p align="center">
  <img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/907bc3a6-7a54-493f-8cd3-f36071554c7a" />
  <br>
  <em>Log Analysis and Event Corellation</em>
</p>
  
## 2. Key Findings from Event Codes

Based on the Splunk dashboard analysis, several critical Event IDs were identified that confirm the progression of the attack:

| Event Code | Count | Description | Security Significance |
| :--- | :--- | :--- | :--- |
| **4624** | 90 | **Successful Logon** | Confirms the attacker successfully bypassed security and gained access to the system. |
| **4672** | 90 | **Special Privileges Assigned** | Indicates the compromised account (`iganteng`) has administrative rights, as elevated privileges were granted immediately after login. |
| **4634** | 76 | **An Account was Logged Off** | Records the termination of RDP sessions, indicating the attacker finished their tasks or disconnected. |
| **4798** | 20 | **Local Group Enumeration** | **Post-Exploitation Activity:** The attacker was performing reconnaissance to identify administrative or high-privileged groups. |
| **7036** | 20 | **Service Status Change** | Indicates that system services were modified, potentially to disable security software or maintain persistence. |

## 3. Deep Dive Analysis
* **The 1:1 Correlation (4624 & 4672):** The identical count (90 events) between Successful Logons and Special
  Privilege assignments is a high-fidelity indicator of **Administrative Login** activity. Every session established by the attacker carried full administrative control.
* **Privilege Discovery:** The presence of **Event ID 4798** is a critical "red flag." It demonstrates that the attacker 
  didn't just log in, but actively performed enumeration to understand their level of access within the domain environment.
* **Network Evidence (Sysmon Event ID 3):** Correlation with Sysmon logs reveals active network connections from the 
  attacker's IP to the target on port **3389 (RDP)**, providing the final link between the brute-force attempts and the successful remote session.
  

  
