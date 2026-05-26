# 🔴 Incident Response Case Study
## WannaCry Worm Attack — Government Agency Internal Network
**Role:** Cybersecurity Intern  
**Environment:** Federal Government Agency, Malaysia (Headquarters — MIS Section)  
**Date:** Mid-January 2025  
**Severity:** High  
**Status:** ✅ Fully Contained & Resolved  

---

## 📋 Executive Summary

In mid-January 2025, a WannaCry worm infection was detected across multiple workstations within the Administration sector of a federal government agency's headquarters. The attack originated from a phishing email that triggered an automatic download, which then propagated laterally across all machines connected to a shared hub within the same network segment. The incident was identified, investigated, contained, and resolved by the MIS team, followed by full IR documentation and a staff cybersecurity awareness workshop.

---

## 🕐 Incident Timeline

```
Morning, Mid-Jan 2025
│
├── 08:00  User reports PC freezing since morning to MIS Supervisor
│
├── 08:30  MIS team begins initial troubleshooting
│          → Cleared cache folders
│          → Deleted old/junk files
│          → Ran disk cleanup commands
│          → Updated Windows OS, drivers, and software
│          → Issue persists after all standard fixes
│
├── 09:30  Malwarebytes installed and full scan initiated
│          → Scan detects WannaCry worm on affected workstation
│
├── 10:00  Investigation expands to all Admin sector workstations
│          → Multiple users report same symptoms simultaneously
│          → User interview conducted — phishing email identified as root cause
│
├── 10:30  Root cause confirmed — phishing link triggered auto-download
│          → Worm propagated via shared hub across Admin sector network
│
├── 11:00  Containment begins
│          → All Admin sector users asked to step away from workstations
│          → Network disabled for affected segment
│
├── 11:30  Remediation begins on root cause machine first
│          → Malwarebytes removal, cache/file cleanup, OS update
│          → Phishing email screenshot taken for documentation
│          → Email sender reported and email deleted
│
├── 12:00 – 17:00  Repeated remediation on all affected workstations
│          → Each machine treated individually
│          → Network rebuilt with new IP scheme
│          → VLAN trunking configured
│          → Unique network IDs assigned per machine
│          → Additional security measures applied
│          → DNS flushed on all machines
│
├── End of Day  All machines cleared and network restored
│
└── Post-Incident
           → Full IR documentation produced per standard guidelines
           → Report submitted to management
           → Cybersecurity awareness workshop conducted for Admin staff
```

---

## 🔍 Phase 1 — Detection

### Initial Report
A user from the Administration sector contacted the MIS Supervisor reporting that her workstation had been freezing since she arrived that morning. She confirmed that everything had been working normally the previous day.

### Initial Troubleshooting
The MIS team performed standard first-response steps:
- Cleared all cache folders and temporary files
- Removed old and redundant files to free up storage
- Ran disk cleanup commands
- Updated Windows OS, hardware drivers, and all installed software to latest versions

Despite all standard troubleshooting steps, the performance issue persisted — pointing toward either a hardware failure (end-of-life) or a malware infection.

### Malware Scan
Malwarebytes was installed and a full system scan was executed. The scan returned a positive detection — the workstation was infected with **WannaCry**, a well-documented ransomware worm known for its ability to self-propagate across networks.

---

## 🔎 Phase 2 — Investigation & Root Cause Analysis

### Scope Expansion
Upon confirmation of the WannaCry infection on the initial machine, the investigation was immediately expanded to all workstations within the Administration sector — the same network segment as the infected machine.

Shortly after, multiple Admin sector employees approached the MIS team independently, reporting the same symptoms — confirming the infection had spread laterally across the sector.

### User Interviews
The team conducted interviews with all affected users, asking specifically about any unusual activity from the previous evening. One user disclosed that she had received an email claiming her account password had been compromised and that she needed to click a link to change it. Upon clicking, the link automatically downloaded a file. As nothing visually changed on her screen, she dismissed it and continued working.

### Root Cause Confirmed
The downloaded file was the WannaCry worm delivery mechanism. Once executed on the initial machine, the worm propagated laterally to all other workstations connected to the same **shared network hub** within the Administration sector.

**Attack Chain:**
```
Phishing Email Received
        ↓
User Clicks Malicious Link
        ↓
WannaCry Payload Auto-Downloaded & Executed
        ↓
Worm Scans Local Network for Vulnerable Machines
        ↓
Propagates via Shared Hub to All Admin Sector Workstations
        ↓
Multiple Machines Infected Simultaneously
```

> **Key Note:** The shared hub architecture within the Admin sector allowed the worm to reach all connected machines without any segmentation barriers. The infection was naturally limited to this segment as it was not connected to other departments — which significantly assisted containment efforts.

---

## 🛡️ Phase 3 — Containment & Remediation

### Immediate Containment
- All Administration sector users were politely asked to step away from their workstations immediately
- The network segment was fully disabled to prevent any further propagation

### Root Cause Machine — Priority Treatment
The workstation belonging to the user who clicked the phishing link was treated first as the highest priority:
- Full Malwarebytes scan and malware removal
- Cache and file cleanup
- Windows OS and software updates applied
- Phishing email **screenshot captured** for documentation purposes
- Phishing email sender **reported** to relevant authorities
- Malicious email **deleted** from the inbox

### Network Rebuild
Rather than simply restoring the old network configuration, the team took the opportunity to rebuild the segment more securely:
- **Existing network fully disabled**
- **New IP address scheme assigned** — unique IDs assigned per workstation for easier monitoring and traceability
- **VLAN trunking configured** between network segments
- **IPRIP/RIP routing** applied for controlled inter-segment communication
- **Additional access controls and security measures** applied at the network level
- **DNS flushed** on all affected machines to eliminate any cached malicious entries

### Workstation Remediation
Each affected workstation was treated individually in sequence:
- Malwarebytes scan and removal
- Cache and file cleanup
- OS and software updates
- Reconnected to the newly configured secure network

> **Note:** The repetitive nature of treating each machine individually was time-consuming. Several workstations experienced significant data loss — work files destroyed and applications severely impacted. This reinforced the importance of regular backups, which was included in subsequent recommendations.

---

## 📝 Phase 4 — Documentation & Post-Incident Actions

### IR Documentation
Upon completion of containment and remediation, a full Incident Response report was produced in accordance with standard IR guidelines and submitted to management. The report covered:
- Incident timeline
- Root cause analysis
- Affected systems inventory
- Containment and remediation steps taken
- Recommendations for prevention

### Cybersecurity Awareness Workshop
Recognising that the human element was the root cause of the attack, the team organised and conducted a cybersecurity awareness workshop for all Administration sector staff. Topics covered:
- How to identify phishing emails
- Safe practices for handling suspicious links and downloadable files
- Recognising social engineering tactics
- What to do if something suspicious is clicked — report immediately, do not dismiss
- Real-world examples of scams targeting office workers

---

## 📚 Lessons Learned

### Technical
- **Network segmentation is critical** — the hub-based flat network allowed unrestricted lateral movement. VLAN implementation significantly reduces blast radius in future incidents
- **Endpoint protection should be standard** — Malwarebytes was installed reactively. Proactive endpoint security solutions should be deployed across all workstations
- **Patch management matters** — keeping OS and software updated reduces the attack surface for known exploits like WannaCry
- **DNS flushing** is an important but often overlooked step in worm containment
- **Unique machine identifiers** in the network configuration make monitoring and future incident tracing significantly faster

### Procedural
- **Backups are non-negotiable** — several users lost work completely. A regular backup policy would have reduced the impact significantly
- **User reporting culture** — the delayed reporting of the suspicious email download extended the window of infection. A culture of immediate reporting is essential
- **IR documentation from day one** — having a clear IR template and process made the post-incident report structured and efficient

### Personal
This was my first real-world cybersecurity incident. The initial discovery was stressful — WannaCry is a well-known and serious threat, and the stakes in a government environment are high. However, applying structured IR methodology — detect, investigate, contain, remediate, document — allowed the team to work through it systematically. The experience confirmed that real-world incident response requires both technical skill and composure under pressure, and it significantly shaped my approach to cybersecurity as a discipline.

---

## 🔧 Tools & Techniques Used

| Tool / Technique | Purpose |
|---|---|
| Malwarebytes | Malware detection and removal |
| Windows Event Logs | System investigation |
| Disk Cleanup Commands | Initial troubleshooting |
| VLAN Trunking | Network segmentation post-incident |
| IP Reassignment | New secure network configuration |
| IPRIP / RIP Routing | Inter-segment routing control |
| Flush DNS | Clearing cached malicious entries |
| User Interviews | Root cause investigation |
| IR Documentation | Standard incident reporting |

---

## ⚠️ Disclaimer

> This case study has been written from personal experience during a cybersecurity internship at a Malaysian federal government agency. All identifying information including agency name, specific IP addresses, system names, usernames, and internal network details have been intentionally omitted or anonymised in compliance with government data confidentiality requirements. This document is intended solely as a professional portfolio piece demonstrating incident response methodology and experience.

---

*Written by Shahrul Haiqal Sipaun — Cybersecurity Graduate, UniKL MIIT*  
*GitHub: github.com/Onn-his-onn-world*
