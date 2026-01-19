#  End-to-End Incident Response & Forensics Lab

This project demonstrates a full end-to-end incident response workflow using a Windows endpoint monitored by Wazuh SIEM.  
The lab simulates a **brute-force authentication attack**, followed by **post-compromise reconnaissance**, **data staging**, **forensic evidence preservation**, **timeline reconstruction**, and a **formal SOC incident report**.

The goal of this lab is to demonstrate practical SOC analyst and DFIR skills, focusing on investigation quality, evidence handling, and clear documentation — not just tool usage.

---

##  Lab Environment

- **SIEM:** Wazuh (Ubuntu VM)
- **Endpoint:** Windows 10 VM with Wazuh Agent
- **Logs & Telemetry:**
  - Windows Security Event Logs
  - PowerShell Operational Logs
  - Sysmon
  - Wazuh File & Registry Integrity Monitoring
- **Tools Used:**
  - Wazuh Dashboard
  - Windows PowerShell
  - VS Code (timeline & incident report)

---

##  Skills Demonstrated

- SIEM monitoring and alert triage  
- Brute-force authentication detection (Event ID 4625)  
- PowerShell attack detection and analysis  
- File and registry integrity monitoring  
- Evidence preservation and chain of custody  
- Cryptographic hashing (SHA256)  
- Incident timeline reconstruction  
- SOC-style incident reporting  

---

##  Incident Response Walkthrough (Step-by-Step)

---

### Lab Preparation
A dedicated incident response working environment was prepared on the Windows endpoint to ensure a structured investigation.

![Lab Preparation](screenshots/00-windows-ir-lab-environment-initialisation.png)

---

### Network Connectivity Verification
Connectivity between the Windows endpoint and the Ubuntu SIEM server was verified to ensure reliable telemetry delivery.

![Network Connectivity Verification](screenshots/01-network-connectivity-windows-to-siem.png)

---

### Wazuh Agent Verification
The Windows endpoint was confirmed as active and reporting within the Wazuh dashboard.

![Wazuh Agent Active](screenshots/02-wazuh-agent-active-windows-endpoint.png)

---

### Baseline Telemetry Validation
Normal Windows events were reviewed prior to attack simulation to establish a clean baseline.

![Baseline Telemetry Validation](screenshots/03-wazuh-baseline-events-windows-endpoint.png)

---

### Sensitive Data Creation
A simulated sensitive dataset was created on the Windows host to represent a realistic attacker objective.

![Sensitive Data Creation](screenshots/04-sensitive-data-creation-windows-endpoint.png)

---

### Brute-Force Authentication Simulation
Multiple failed authentication attempts were generated, simulating a brute-force attack against a local user account.

![Brute-Force Authentication](screenshots/05-bruteforce-authentication-events-detected-wazuh.png)

---

### Post-Compromise Reconnaissance
PowerShell reconnaissance commands were executed to enumerate user context, system identity, network configuration, and privileges.

![Post-Compromise Reconnaissance](screenshots/06-post-compromise-reconnaissance-powershell.png)

---

### Data Staging & Compression
Sensitive data was staged in a public directory and compressed into an archive (`loot.zip`), simulating preparation for exfiltration.

![Data Staging and Compression](screenshots/07-data-staging-and-archive-creation.png)

---

### Brute-Force Validation (Event ID 4625)
Windows Security Event ID **4625** was analysed to confirm repeated authentication failures consistent with brute-force behaviour.

![Event ID 4625 Analysis](screenshots/08-failed-logon-eventid-4625-analysis.png)

---

### System Integrity Monitoring
Wazuh File and Registry Integrity Monitoring detected a registry modification, confirming system-level changes during the incident.

![Registry Integrity Monitoring](screenshots/09-registry-integrity-modification-detected-wazuh.png)

---

### Forensic Evidence Preservation
Relevant Windows event logs were exported in native EVTX format to preserve forensic evidence.

![Forensic Evidence Collection](screenshots/11-forensic-evidence-collection-windows-evtx.png)

---

### Evidence Integrity Verification
SHA256 hashes were generated for all critical forensic artifacts to maintain chain-of-custody integrity.

![SHA256 Hash Verification](screenshots/12-sha256-hash-verification-evidence.png)

---

### SIEM Evidence Export
Relevant Wazuh alerts were exported into an on-demand report for offline analysis and documentation.

![SIEM Evidence Export](screenshots/13-wazuh-alerts-exported-incident-evidence.png)

---

### Incident Timeline Reconstruction
A complete incident timeline was reconstructed by correlating Windows logs, PowerShell activity, and Wazuh alerts.

![Incident Timeline Reconstruction](screenshots/14-incident-timeline-reconstruction.png)

---

### Final SOC Incident Report
A full L1 SOC-style incident report was produced, documenting findings, impact assessment, and response recommendations.

![Final SOC Incident Report](screenshots/15-final-soc-incident-report-authentication-anomaly.png)

---

## Key Takeaway

This lab demonstrates a realistic end-to-end incident response workflow:

**Detection → Investigation → Forensics → Evidence Integrity → Timeline → Reporting**

The project reflects real SOC and DFIR practices, making it suitable for junior SOC analyst and incident response roles.
